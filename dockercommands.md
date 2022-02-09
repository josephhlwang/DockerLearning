# Docker Commands

Docker commands cheatsheet. Used for building, running and maintaining Docker containers.

### Dockerfile instructions

`FROM` : to specify the base image

`WORKDIR` : to set the working directory

`COPY` : to copy files/directories

`ADD` : to copy files/directories

`RUN` : to run commands

`ENV` : to set environment variables

`EXPOSE` : to document the port the container is listening on

`USER` : to set the user running the app

`CMD` : to set the default command/program

`ENTRYPOINT` : to set the default command/program

### Image commands

`docker build -t <name> .` : to build image

`docker images` : to list images

`docker run -it <image> sh` : to run image on new container with interactive shell

`docker image prune` : to delete unused image
