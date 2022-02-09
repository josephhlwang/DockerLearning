# Docker Notes

Docker notes for: https://www.youtube.com/playlist?list=PLy_6D98if3ULEtXtNSY_2qN21VCKgoQAE and https://www.youtube.com/watch?v=pTFZFxd4hOI

Docker: https://www.docker.com/get-started

### What is Docker?

A way to build, run and ship applications consistently. Docker allows multiple versions of applications to run side by side, each with its own dependencies/environments.

Docker is similar to a VM but a VM needs an OS, is slow to start and resource intensive.

### Docker Architecture

Docker is a client/server application that uses REST to communicate.

The server, called the Docker Engine, takes care of running containers which are processes of applications. All containers share the OS kernel.

Each container has it's own ports, host ports must be mapped to container ports.

### Pulling DockerHub Images

Public images like mysql can be pulled from [DockerHub](https://hub.docker.com/).

Use `docker pull <image_name>` to pull image from repo.

### Setting Up Your Own Docker Images

To dockerize an application, add a _Dockerfile_ that contains instructions to package the application into an image.
To reduce image size, add files/folders to ignore in image t _.dockerignore_. Dependencies/libraries should be excluded.

Check _dockercommands.md_ for full commands.

1. FROM -to define base image
2. WORKDIR -to define root workdir
3. COPY -defind what files to copy
4. RUN -run sh code to install dependencies
5. ENV -set environment variables
6. EXPOSE -documentating image port
7. ENTRYPOINT -define default "startup" command

Build docker image with `docker build -t <image_name> .`.

### Optimizing Your Own Image Build In _Dockerfile_

Each command in the _Dockerfile_ creates a new layer in the file system of the image. Since Docker can cache unchanged parts of the file system when creating a new build, write the most stable instructions first, then the less stable instructions.

Eg. copy and install the dependencies before copying the rest of the app files.

### Running Docker Containers

After building an image, run the image in a container in the background using `docker run -d -p 80:3000 <imageID>` while mapping port 80 on the host to port 3000 on the container.

Check its logs using `docker logs -f <containerID>`.

To execute a single command in the `WORKDIR` in a running container use `docker exec <containerID> <command>`. To start a shell session in the container, use `docker exec -it <containerID> sh`.

To (re)start and stop containers use `docker start <containerID>` and `docker stop <containerID>`.

### Docker Volumes

Persisting data should not be stored in the containers but in _volumes_. Deleting the container will not effect the volume it was initialized on.

Create a new volume with `docker volume create <volumeName>`.

After building an image, run the image with an volume use `docker run -d -p 80:3000 -v <volumeName>:<containerPath> <imageID>`.

Be careful of file premissions when using volumes.
