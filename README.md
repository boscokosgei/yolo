# Overview
This project involved the containerization and deployment of a full-stack yolo application using Docker.


# Requirements
Install the docker engine here:
- [Docker](https://docs.docker.com/engine/install/) 

## How to launch the application 


![Alt text](image.png)

## Stage 1 Ansible Instrumentation


## Initializing the Vagrant 
  from hashicorp registry we pick ubuntu/jammy64 box
```sh
    vagrant init ubuntu/jammy64
```
## How to run the app
Use vagrant up --provison command
```sh 
    vagrant up
```
## SSH into the Server 
```sh
    vagrant ssh

```
## running Ansible Playbook
 This is provisioning of Ubuntu/jammy64 Server to install docker and pull container images from Dockerhub to run Application inside VM
```sh 
   ansible-playbook playbook.yml hosts
```
## Stage 2 Ansible and Terraform Instrumentation
 creating a Branch to work on terraform file
```sh
    git checkout -b stage_two

```
## Installing Terraform
```sh 
   sudo apt update
   sudo snap install terraform --classic
```
## Creating Terraform Scripts
```sh
    touch main.tf
    touch variables.tf
    touch outputs.tf
    touch terraform.ftvars
```
## Running Terraform To Initiate
 to check if everything is okay
```sh
    terraform plan 
```

 To Initialise terraform
 ```sh
    terraform init
 ```
 To provision the Server
 ```sh
    terraform apply
 ```

