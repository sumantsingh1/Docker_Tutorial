#### What is Docker Volumes?
```sh
Doker container filesystem is ephemeral.
Its deleted with the container
To run stateful application such as Jenkins, daabase
Note: Stateful application stores its state in data in local
```
#### Without Volume
```sh
# Start a Jenkins container in detached mode
docker run -d -p 8080:8080 --name myjenkins jenkins/jenkins

# Access the command line interface of the running Jenkins container
docker exec -it myjenkins /bin/bash

```
#### With Volume
```sh
# Create a Docker volume named 'jenkins'
docker volume create jenkins

# Start a Jenkins container in detached mode with a mounted volume for persistent data
docker run -d -p 8080:8080 --name jenkins -v jenkins:/var/jenkins_home jenkins/jenkins

```
