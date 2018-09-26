# Dockerfile

Dockefile is created on top of `ubuntu:latest` image.

Git and other basic developer tools are available in the image.

# Quick Start

- Unzip `End2End-Docker.zip` in `end2end` folder
- Open a terminal session to that folder
- Navigate to ```docker``` directory.
- Run `docker-compose build`
- Run `docker-compose up -d`
- Run `docker exec -it end2end bash`
- At this point you must be inside the docker container, in the root folder of the project. From there, you can build the repository as usual:
	- `cd /app && ./do.sh install_deps`
	- `./do.sh build_app`
	- Now you can run the application by executing `./do.sh testserver`
	- To access running instance, navigate to 'http://localhost:8000'
- When you finish working with the container, type `exit`
- Run `docker-compose down` to stop the service.

## Build the image

In `end2end/docker` folder, run:

```bash
docker-compose build
```

This instruction will create a DockerImage in your machine called `end2end_builder:latest`

## Run the container

In `end2end/docker` folder, run:

```bash
docker-compose up -d
```

Parameter `-d` makes the container run in detached mode.
This command will create a running container in detached mode called `end2end`.
You can check the containers running with `docker ps`

## Get a container session

Run:

```bash
docker exec -it end2end bash
```

Parameters `-it` allocate an interactive TTY session

## docker-compose.yml

The docker-compose.yml file contains a single service: `builder`.
We will use this service to run end2end from our local environment, so we mount root project dir `./end2end` to the a `/app` folder:

```yaml
    volumes:
      - ..:/app:Z
```

## Requirements
The container was tested successfully on:
- Docker 17.05 and up
- docker-compose 1.8 and up

