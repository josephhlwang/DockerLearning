# Docker Compose Notes

Docker-compose notes for: https://www.youtube.com/watch?v=pTFZFxd4hOI

Docker: https://www.docker.com/get-started

### What is Docker-compose?

Docker compose is a tool for running multi-container applications. It creates a way to easily startup and manage mutiple services of a single application.

Ex. Start front-end server, back-end server and db at the same time.

In a folder with mutiple _Dockerfiles_ for each service, using the _docker-compose.yml_ file, you can setup the start-up process of the application as a whole. The setup for the build of each service is still implemented in the _Dockerfile_ of each service.

### Setting Up _docker-compose.yml_

In the root folder of the application, create a new file named _docker-compose.yml_.

Put the version number in `version:`, services of application in `services:` and volumes in `volumes:`.

Example of a _docker-compose.yml_.

```yaml
version: "3.8"

services:
  frontend:
    depends_on:
      - backend
    build: ./frontend
    ports:
      - 3000:3000
    volumes:
      - ./frontend:/app

  backend:
    depends_on:
      - db
    build: ./backend
    ports:
      - 3001:3001
    environment:
      DB_URL: mongodb://db/vidly
    command: ./docker-entrypoint.sh
    volumes:
      - ./backend:/app

  db:
    image: mongo:4.0-xenial
    ports:
      - 27017:27017
    volumes:
      - vidly:/data/db

volumes:
  vidly:
```

In each service defined in `services:`:

- use `depends_on:` to define order of container startup.
- use `build:` to define path of service src.
- use `image:` to define image of service.
- use `ports:` to define mapping of host ports to container ports.
- use `volumes:` to define mapping of volumes.

### Building and Starting Up Containers

Pretty much all commands usable in Docker are usable in Docker-compose.

To build the images use `docker-compose build`.
To build and start the images in containers use `docker-compose up`.
To start and stop the containers use `docker-compose start` and `docker-compose stop`.
To view logs use `docker-compose logs`
