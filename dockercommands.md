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

### Starting and stopping containers

`docker stop <containerID>` : to stop container

`docker start <containerID>` : to stop container

`docker logs -f <containerID>` : to follow container logs(output)

### Removing containers

`docker container rm <containerID>` : to remove container

`docker rm <containerID>` : to remove container

`docker rm -f <containerID>` : to force remove container

`docker container prune` : to remove stopped containers

### Volumes

`docker volume ls` : to list volumes

`docker volume create app-data` : to create new volume

`docker volume inspect app-data` : to inspect metadata of volume

`docker run -v app-data:/app/data <image>` : to run container with volumn

### Copying files between the host and containers

`docker cp <containerID>:/app/log.txt .` : to copy file from container to host

`docker cp secret.txt <containerID>:/app` : to copy file from host to container

### Sharing source code with containers

`docker run -v $(pwd):/app <image>`

### Docker-compose

`docker-compose build` : to build images

`docker-compose build --no-cache` : : to build images without using cached files

`docker-compose up` : to build images if not built and start containers

`docker-compose up -d` : to build images if not built and start containers in detached mode

`docker-compose up —build` : to force build images and start p containers

`docker-compose down` : to stop and remove containers

`docker-compose start` : to start containers

`docker-compose stop` : to stop containers

`docker-compose ps` : to list containers

`docker-compose logs` : to show combined logs of all containers
