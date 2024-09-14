# Go Application with Docker

This repository contains a Go application containerized using Docker. The Docker setup includes building the Go binary in a multi-stage build and running it in a minimal `debian:buster-slim` environment.

## Prerequisites

Make sure you have the following installed:
- [Docker](https://docs.docker.com/get-docker/)

## Build and Run the Docker Container

### Step 1: Build the Docker Image

To build the Docker image for your Go application, run the following command:

```bash
docker build -t go-buster-slim-test .
```
This will create a Docker image tagged as go-buster-slim-test using Go 1.22.4.

### Step 2: Run the Docker Container

To run the Docker container and expose the app on port 1323, use this command:

```bash
docker run --name go-buster-app -p 1323:1323 -d go-buster-slim-test
```

- --name go-buster-app: Names the container as go-buster-app.
- -p 1323:1323: Maps the container's port 1323 to your host's port 1323.
- -d: Runs the container in detached mode.

### Step 3: Access the Application

Once the container is running, you can access the application in your browser at:
```
http://localhost:1323
```

### Stop and Remove the Container
To stop the running container:
```bash
docker stop go-buster-app
```

To remove the container:
```bash
docker rm go-buster-app
```

### Cleanup
If you want to remove the Docker image as well:

```bash
docker rmi go-buster-slim-test
```