##Here are the two ways to create and interact with Docker containers:

### 1. Detached Mode (Background)
```sh
# Run an Nginx container in detached mode and map port 80 of the host to port 80 of the container
docker run -d -p 80:80 nginx

```
### 2. Interactive Mode
```sh
# Run an Nginx container interactively and map port 80 of the host to port 80 of the container
docker run -it -p 80:80 nginx bash

```
### Exit Interactive Mode Without Stopping the Container:
```sh
# Use this key combination to exit the container and leave it running
ctrl + p + q
```
### Re-enter a Running Container:
```sh
# Log back into the running container from the Docker host
docker exec -it <container id> bash

```
### Run in Detached and Interactive Mode Combined:
```sh
# Run an Nginx container in both detached and interactive mode
docker run -itd -p 80:80 nginx
```

#### How to create container
```sh
# Run an Nginx container in detached mode, map port 80 of the host to port 80 of the container, and name the container "mynginx"
docker run -d -p 80:80 --name mynginx nginx

# Run a container from the "amiyaranjansahoo/myapp:v1" image in detached mode, mapping port 8080 of the host to port 8080 of the container
docker run -d -p 8080:8080 amiyaranjansahoo/myapp:v1

# Run an interactive container from the "amiyaranjansahoo/img1:v1" image, with a Bash shell for interaction
docker run -it amiyaranjansahoo/img1:v1 bash

```
#### List the containers
```sh
# List all running containers
docker ps  # Same as: docker container ls

# List all containers, including stopped ones
docker ps -a  # Same as: docker container ls -a

```
#### List the Docker images
```sh
# List all Docker images on your system
docker images  # Same as: docker image ls

```
#### Delete the containers
```sh
# Delete a stopped or exited container
docker rm <container id>  # Removes containers that are not running

# Forcefully delete a running container
docker rm -f <container id>  # Forcefully removes a container, even if it is running

```
#### Delete the images
```sh
# Delete a Docker image by its ID
docker rmi <image id>
```
#### Container Logging information
```sh
# View logs of a container using its container ID
docker logs <container id>

# View logs of a container using its container name
docker logs <container name>

```
#### Monitoring the CPU and Memory of docker container
```sh
# Display real-time statistics (CPU, memory, etc.) for running containers
docker stats  # Shows default memory limit, typically 949.6MiB

# Run an Nginx container in detached mode, map port 80 of the host to port 80 of the container, 
# set a memory limit of 200MiB, and name the container "mynginx"
docker run -d -p 80:80 --memory=200MiB --name mynginx nginx

* The docker stats command provides real-time performance data for all running containers.
* The --memory=200MiB option limits the container's memory usage to 200MiB.
```
