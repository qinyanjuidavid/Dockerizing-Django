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

- Docker Image - is the actual package.In other terms it is the artifact that can be moved around eg.postgres.
- Docker Container - actually start the application. Container is where the environment of an application is created.
