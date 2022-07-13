# Docker-Learning

> A container is a way to package application with all the necessary dependencies and configurations

- A container is Portable artifact, easily shared and moved around
- Containers live in Container Repository. There are both private repositories and public Repository for Docker. Go to _Docker Hub_
- A container is a layer of images

  1. Layer- application image (eg. PostgreSQL,Redis)
  2. Layer- Linux Base image (Alpine:3.10- Because it is small in size)

- `docker pull postgres` In order to pull the an image from the public repository, You can specify the version `docker pull postgres:14.4`
- `docker ps` To view the number image running locally

### Docker Image and Docker Container

- Docker Image - is the actual package.In other terms it is the artifact that can be moved around eg.postgres
- Docker Container - actually start the application Container is where the environment of an application is created
- Container is a running environment for Image
- Application images include: postgres,regis, mongodb
- Containers have a port binded to it. A port enables the applications running inside the container to talk to each other

### Docker vs Virtual Machine

- An Operating system is made up of the Appplications, Os Kernel and Hardware Layer

- Operating System Kernel communicates with the Hardware Layer like CPU,memory,etc
- Applications run on the Application Layer
- Docker virtualizes the applications layer. It uses the Kernel of the host because it does not have its own Kernel
- VM virtualizes the Applications layer and the Operating System Kernel. When you install the Virtual Machine Image it boots its own kernel and does not use the host Kernel
  1. Docker Images are much small the VM are large in size
  2. Docker containers start and run much fast than the VM, since each time you start a VM it has to boot it's own kernel
  3. VM of any OS can run on any Operating System host but that can't happen with docker.

### Docker Installation

- Docker Toolbox helps check the machine compactibility. Docker Toolbox helps run docker natively.

### Basic Docker Commands

- `docker pull nameOfImage` or `docker pull namerOfImage:7.0.3` To pull image from docker hub to the local machine
- `docker images` Used when checking all the images on the local machine
- `docker run redis` Creates a container where redis is running and can be used in an application
- `docker ps` used to check the containers that are running locally
- `docker run -d redis` Used to run a container a dettached mode. Meaning that the container will run even after closing the terminal
- `docker stop idOfTheContainer` The id is the first part you view when you use the `docker ps` command
- `docker start idOfTheContainer` You can use the same id as above to start the container
- `docker ps -a` To see all the containers that are running of not running
- `docker run -p 6000:6379 redis` or `docker run -d -p 6000:6379 redis' to be able to run two containers that uses the same port
  - `-p` is the port
  - `6000` is the host port
  - `6379` container port
- `docker run -d -p 6001:6379 --name redis-older redis:7.0.3` Naming the container for instance redis-older

### Container Ports Vs Host Port

- Multiple Containers can run on your host machine
- Conflict when same port on host machine
- The applications can't be able to reach the containers using same port

### Debugging Containers

- `docker logs containerID/conteinerName` to check the logs of the container
- `docker exec -it containerID/containerName /bin/bash`
  - `it` Interactive terminal

### Demo Project Overview

- Postgres/Mongo DB- Push to Git where Jenkins Builds Django App and Creates Docker Image
- The Docker image built by Jenkins is pushed to a private docker repository
- The Docker image is pulled to the development server where they talk to each other with the django app

### Developing with Containers

- Hands on Code

### Docker Network

- Docker creates it's own isolated network where the containers are running
- Those containers can talk to each other using container name
- `docker network ls` shows auto generated networks
- 'docker network create mongo-network' creating a docker network
- `docker network rm NameOfTheNetwork` To delete a network

### Docker Postgres

- `docker run --name some-postgres --network postgres-network -e POSTGRES_PASSWORD=nonerd -e POSTGRES_USER=day -d postgres`
  - `--name (som-postgres)` name of the container
  - `--network (postgres-network)` name of the network
  - `-e` Environment Variables
    - Postgres Password
    - Postgres User
  - `-d` running the container in dettache mode

### Dockerizing Django

- `docker-compose run web django-admin startproject src .` Starting the project
- `docker-compose up` to run the project
- `docker-compose down` To stop the project
