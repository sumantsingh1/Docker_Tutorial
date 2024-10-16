#### What is Dockerfile?
```sh
Dockerfile is basically a text file, 
It contains some set of instructions
Automation of Docker image creation
```
### FROM 
```sh
It is used to define the base image for the container
```
### LABEL 
```sh
It is for describing teh metadata
```
### RUN
```sh
It's used to execute the commands
It works at build(image)time
For example installing a package , downloading the files etc
```
### COPY 
```sh
It's used to copy files from local systems (docker VM) to docker image
It works at build(image)time
```
### ADD
```sh
It provides a feature to download files from internet
```
### EXPOSE
```sh
To expose ports such as port 8080 for tomcat,
```
### WORKDIR
```sh
To set the working directory for a container
```
### ARG
```sh
Use build-time variables
```
### ENV
```sh
To set the environment variable at runtime
```
### CMD
```sh
Execute commands but during container creation
It works at run(container) time
# FROM ubuntu
# CMD ["echo","Welcome to docker"]
# docker run -it <container_id>
# docker run -it <container_id> echo "welcome to aws"
# docker run -it <container_id> uname
```
### ENTRYPOINT
```sh
Similar to CMD, but has higher priority over CMD
# FROM ubuntu
# ENTRYPOINT echo "Welcome to docker"
# docker run -it <container_id> echo 'Welcome to aws'
```
### CMD and ENTRYPOINT
```sh
FROM ubuntu
ENTRYPOINT ["echo"]
CMD ["Welcome to Docker"]
```

### Sample Dockerfile
```sh
https://github.com/amiyaranjansahoo/docker-cicd-students-demo.git
ARG version=3.14.1
FROM alpine:${version}
LABEL name="java home"
RUN apk add openjdk8

# Download and install tomcat8
WORKDIR /root/RnD
RUN wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.91/bin/apache-tomcat-9.0.91.tar.gz
RUN tar -xvf apache-tomcat-9.0.91.tar.gz
RUN mv apache-tomcat-9.0.91 tomcat9

EXPOSE 8080

# Create the staic page
WORKDIR /root/RnD/tomcat9/webapps
RUN mkdir amiya
RUN echo "<h2> Welcome to the Docker technology - V1 </h2>" > amiya/index.html
CMD ["/root/RnD/tomcat9/bin/catalina.sh","run"]
```
### Multi stage docker build
```sh
https://github.com/amiyaranjansahoo/multi-stage-spring-boot-docker

# First stage: build the application with Maven

FROM maven:3.8.3-openjdk-17 AS builder
WORKDIR /app
COPY pom.xml .
RUN mvn dependency:go-offline
COPY src/ /app/src/
RUN mvn package

# Second stage: run the application with OpenJDK

FROM openjdk:17-jdk-slim
WORKDIR /app
COPY --from=builder /app/target/api-0.0.1-SNAPSHOT.jar .
EXPOSE 8080
CMD ["java", "-jar", "api-0.0.1-SNAPSHOT.jar"]
```






