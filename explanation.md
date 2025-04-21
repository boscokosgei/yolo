
# Docker Containerisation and  Docker Orchestration Explanation
Project to create docker containers and automate the deployment process for managing containers through docker-compose.yml,docker networking and working with docker volumes.


## Prerequisites
- A Github account
- Dockerhub account(to get image from registry)
- Mongodb account(for database application)
- Container Networking
- Docker Volume Understanding
- Render Account(Deployment)
- Git Workflows
- Docker Orcehstration

Step 1:Forking and cloning the repository
   Navigate to the link shared to fork the project
```bash
git clone htttps://boscokosgei@github.git
```
## Choosing the base image on building the containers
There are some factor to consider for choosing an image
 we create an image from docker registry alpine as the choice of image
 since its lightweight and the image size is small as well as versioning
 We will use alpine as its small and lightweight
 adding dockeringore file to reduce the size of the image
```bash
   FROM node-16:alpine
```
```sh
touch .dockerignore
```
## Docker directives used in the creation and running each container

Creating the backend and frontend of the Containers
in Dockerfile
```sh FROM node:16-alpine AS build 
```
## Docker-compose Networking
This is used to create network and assign  IP to enable communication between containers
```bash
docker create network
```

## Docker-compose volume definition and usage
Attaching a local storage for data to persist

## Git workflow used to achieve the task



