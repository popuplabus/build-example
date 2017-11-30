Docker build-example 
=========

Getting started
---------------

Go to [Play with Docker](https://www.play-with-docker.com). Add 2 New Instances. 

Run these commands in your first instance:
```
git clone https://github.com/popuplabus/build-example.git
cd build-example
ls

docker image ls

cat Dockerfile
```

Dockerfile should have the following text:

  FROM openjdk:7

  COPY src /usr/src/myapp

  WORKDIR /usr/src/myapp

  RUN javac HelloPortsmouth.java

  CMD ["java", "HelloPortsmouth"]


* Step 1 - Build:
```
docker build -t hello-portsmouth-image .
```
* Step 2 - Ship:
```
docker login -u popuplabus -p <password>
docker tag hello-portsmouth-image popuplabus/hello-portsmouth-image:<your own initials>
docker image ls

docker push popuplabus/hello-portsmouth-image:<your own initials>
```

Go to [Docker Hub](https://hub.docker.com/r/popuplabus/hello-portsmouth-image/). View the Tags.

Run in these commands in your second instance:

* Step 3 - Run:
```
docker image ls
docker container ls -a

docker container run --name my-hello-portsmouth popuplabus/hello-portsmouth-image:<your own initials> 

docker image ls
docker container ls -a
```
