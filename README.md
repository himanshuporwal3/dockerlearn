# Docker Learn
# Installing Docker

In this lesson, we'll install the latest version of Docker CE. The commands used through out out this video are below.

## Prerequisites

Uninstall old versions:

```
sudo yum remove -y docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

## Install Docker CE

Add the Utilities needed for Docker:

```
sudo yum install -y yum-utils \
  device-mapper-persistent-data \
  lvm2
```

Set up the `stable` repository:

```
sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
```

Install Docker CE:

```shell
sudo yum -y install docker-ce
```

Enable and start Docker:

```dockerfile
sudo systemctl start docker && sudo systemctl enable docker
```

Add `cloud_user` to the `docker` group:

```dockerfile
sudo usermod -aG docker cloud_user
```

# Docker Architecture

In this lesson we will take a high-level look at the Docker Architecture.

## Architecture Overview

Docker architecture:

- Client-server architecture
- Client talks to the Docker daemon
- The Docker daemon handles:
  - Building
  - Running
  - Distributing
- Both communicate using a REST API:
  - UNIX sockets
  - Network interface

The Docker daemon (`dockerd`):

- Listens for Docker API requests and manages Docker objects:
  - Images
  - Containers
  - Networks
  - Volumes

The Docker client (docker):

- Is how users interact with Docker
- Sends commands to `dockerd`

Docker registries:

- Stores Docker images
- Public registry such as DockerHub
- Let you run your own private registry

Docker objects:

- Images:
  - Read-only template with instructions for creating a Docker container
  - Image is based on another image
  - Create your own images
  - Use images published to a registry
  - Use a Dockerfile to build images
- Containers:
  - Runnable instance of an image
  - Connect a container to networks
  - Attach storage
  - Create a new image based on its current state
  - Isolated from other containers and the host machine
- Services
  - Scale containers across multiple Docker daemons
  - Docker Swarm
  - Define the desired state
  - Service is load-balanced

Docker Swarm:

- Multiple Docker daemons (Master and Workers)
- The daemons all communicate using the Docker API
- Supported in Docker 1.12 and higher

![image-20200606001311820](C:\Users\himan\OneDrive\MS Resources\dockerLearn\dockerlearn\images\image-20200606001311820.png)

![image-20200606001635465](C:\Users\himan\OneDrive\MS Resources\dockerLearn\dockerlearn\images\image-20200606001635465.png)

![image-20200606001840341](C:\Users\himan\OneDrive\MS Resources\dockerLearn\dockerlearn\images\image-20200606001840341.png)