[Link source](https://www.youtube.com/watch?v=pg19Z8LL06w)
# What is Docker?
- Virtualization software
- Makes developing and deploying applications much easier
- Packages application with all the necessary dependencies, configuration, system tools and runtime
- Portable artifact, easy shared and distributed

# Before Containers
Developer have to install all dependencies and configurations locally and for each operating system(OS) It was different but with Docker we install all dependencies and configurations in to containers only one time and run it from internet server.

# How an OS is made up?
OS has 2 main layer:
1. OS Applications Layer
2. OS Kernel
		- Kernel is at the core of every operating system
		- Kernel interacts between hardware & software components

![alt text](<Pasted image 20240430151221.png>)


# Terminal:
- docker images = List all Docker images
- docker ps = List running containers
- docker pull {name}:{tag} = Pull an image from a registry(docker pull nginx:1.23)
- docker run {name}:{tag} = creates a container from given image and starts it
- -d or --detach = Runs container in background and prints the container ID (docker run -d ngnix:1.23)
- docker logs {container} = View logs from service running inside the container. (which are present at the time of execution)(docker logs d50884a3cccb)
- docker stop {container} = Stop one or more running containers(docker stop d50884a3cccb)
-  -p or --publish = Publish a container's port to the post(docker run -d -p 9000:80 nginx:1.23)
- -a or --all = Lists all containers (stopped and running)(docker ps -a)
- docker start {container} = Start one or more stopped containers
- --name = Assign a name to the container(docker run --name web-app -d -p 9000:80 nginx:1.23)
- docker build {path} = Builds a Docker image from a Dockerfile
- -t or --tag = Sets a name and optionally a tag in the "name:tag" format (docker build -t node-app:1.0 .)
# Docker Registries
- A storage and distribution system for Docker images
- Find and share Docker images
- Docker hosts one of the biggest Docker Registry, called "Docker Hub"

 
 ***Note:*** "latest" tag mostly refers to the newest release
 ***Note:*** Docker generates a random name for the container automatically if you don't specify one
 ***Note:*** Docker pulls image automatically, if it doesn't find it locally
 ***Note:*** Only 1 service can run on a specific port on the host So e.g. only 1 service can run on port 9000
 ***Note:*** Standard to use the same port on your host as container is using
 
 
# Container Port vs Host Port
![alt text](<Pasted image 20240430162841.png>)

# Registry vs Repository
## Docker Registry
- A service providing storage
- Collection of repositories
## Docker Repository
- Collection of related images with same name but different versions
![alt text](<Pasted image 20240430171140.png>)
# Dockerfile - Build instruction
- Dockerfile is a text document that contains commands to assemble an image
- Docker can then build an image by reading those instructions

## Structure of Dockerfile
- Dockerfiles start from a parent image or "base image"
- It's a Docker image that your image is based on
- You choose the base image, depending on which tools you need to have available
- FROM:
		- Build this image from the specified image
- RUN:
		- Will execute any command in a shell inside the container environment
- COPY:
		- Copies files or directories from <src> and adds them to the filesystem of the container at the path <dest>
		- While "RUN" is executed in the container, "COPY" is executed on the host
   - WORKDIR:
		- Sets the working directory for all following commands
		- Like changing into a directory: "cd ..."
   - CMD:
	    - The instruction that is to be executed when a Docker container starts
	    - There can be one "CMD" instruction in a Dockerfile

![alt text](<Pasted image 20240430190205.jpg>)