### Docker
```sh
Docker is free and  open-source project 
It is a containerization tool
It is used to build images and run containers.
It packages the OS, application and dependency together
It  automates the deployment of applications as a container
```
### Advantages over virtual machine
```sh
1. Faster Boot Time: Containers can start in seconds (or even milliseconds)
because they don’t need to boot an entire OS. In contrast, VMs take minutes
to boot up since each VM has its own OS.

2. Lightweight: Docker containers share the host OS kernel, allowing multiple containers
to run on a single host without the overhead of a full OS for each instance. This makes
 containers much lighter in terms of both memory and CPU usage compared to VMs.

3. Consistency Across Environments: Docker ensures that the application and its dependencies
are packaged together, making it easy to move containers across different environments
(development, testing, production) without worrying about environment-specific issues.

4. Platform Independence: Docker images can run on any system that supports Docker, providing
a consistent environment regardless of the underlying infrastructure (e.g., local machines,
on-premises servers, or cloud platforms).
```
### Docker Installation (Using the Docker Desktop)
```sh
https://docs.docker.com/desktop/install/windows-install/
```

### Docker Installation (Online platform)
```sh
https://labs.play-with-docker.com/ # Login using the docker hub
```

### Docker Installation (using ec2)
```sh
How to install docker: (Login as ec2-user)
# Install Docker on an Amazon Linux EC2 instance
sudo yum install docker

# Check the Docker version (note: daemon is not running)
docker version # Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?

# Start the Docker service
sudo service docker start

# Enable Docker to start at boot
sudo systemctl enable docker

# List Docker images
docker image ls

# Add the ec2-user to the docker group so you can execute Docker commands without using sudo
# Check group details (confirm docker group exists, and ec2-user is not in the group yet)
cat /etc/group # docker group present and ec2-user does not present to the group

# Add the ec2-user to the Docker group
sudo usermod -G docker ec2-user 

# Verify that the ec2-user is now part of the Docker group
cat /etc/group  # We must see ec2-user belongs to the docker group.

# Logout and login again for group changes to take effect

# List Docker images again, this time without needing sudo
docker image ls

# Run an Ubuntu container in detached and interactive mode
docker run -itd ubuntu

# Alternative solution: allow non-root users to access Docker by modifying socket permissions
sudo chmod  666 /var/run/docker.sock
```
