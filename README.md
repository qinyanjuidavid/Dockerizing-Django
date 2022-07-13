# Docker-Learning

Learning Docker using Tech with Nana tutorial.

## Docker

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

### Docker vs Virtual Machine

- An Operating system is made up of the Appplications, Os Kernel and Hardware Layer

- Operating System Kernel communicates with the Hardware Layer like CPU,memory,etc
- Applications run on the Application Layer
- Docker virtualizes the applications layer. It uses the Kernel of the host because it does not have its own Kernel
- VM virtualizes the Applications layer and the Operating System Kernel. When you install the Virtual Machine Image it boots its own kernel and does not use the host Kernel
  1. Docker Images are much small the VM are large in size
  2. Docker containers start and run much fast than the VM, since each time you start a VM it has to boot it's own kernel
  3. VM of any OS can run on any Operating System host but that can't happen with docker.
