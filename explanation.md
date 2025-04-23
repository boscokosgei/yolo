
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
git clone https://github.com/boscokosgei/yolo.git
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
  use multistage build to reduce the image size
```sh
touch .dockerignore
```
## Docker directives used in the creation and running each container

Creating the backend and frontend of the Containers
in Dockerfile
```sh FROM node:16-alpine AS build 

```
Connecting to MongoDB Database by defining in server.js file
```sh
 let dbName = 'yolomy';
```
Creating the Client Container by updating the Dockerfile to pick image from base image alpine

Creating docker-compose.yml file to orchestrate the containers
Client image to run the frontend and semver image for versioning
```sh
    image: boscokipkosgei/bosco-yolo-client:v1.0.0
```
Backend image to run the backend and semver image for versioning
```sh
    image: boscokipkosgei/bosco-yolo-backend:v1.0.0
```
Mongo DB image for database
```sh
   image: mongo
```
After creation of Containers we build the client image by running Dockerfile on client locally and push it to dockerhub
```sh
   docker build -t boscokipkosgei/bosco-yolo-client:v1.0.0
   docker run -p 3000:3000 boscokipkosgei/bosco-yolo-client:v1.0.0
   docker push boscokipkosgei/bosco-yolo-client:v1.0.0
```
After creation of Containers we build the Backend image by running Dockerfile on backend locally and push it to dockerhub
```sh
   docker build -t boscokipkosgei/bosco-yolo-backend:v1.0.0
   docker run -p 5000:5000 boscokipkosgei/bosco-yolo-backend:v1.0.0
   docker push boscokipkosgei/bosco-yolo-backend:v1.0.0
```
Finally we pull the images from docker hub and run the containers by Orchestration using docker-compose command
```sh
   docker-compose up
```
## Docker-compose Networking
This is used to create network and assign  IP to enable communication between containers
select class B Ip address 172.20.0.0/16
```bash
docker create network
subnet: 172.20.0.0/16
```

## Docker-compose volume definition and usage
Attaching a local storage for data to persist
```sh
volumes:
  app-mongo-data:
    driver: local
```

## Git workflow used to achieve the task



