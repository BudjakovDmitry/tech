# Docker architecture

Docker uses a client-server architecture. The Docker client and Docker daemon can run on
the same system, or you can connect a Docker client to a remote Docker daemon. The
Docker client and daemon communicate using a REST API, over UNIX sockets or a network
interface. Another Docker client is Docker Compose, that lets you work with applications
consisting of a set of containers.

![Docker architecture](images/docker-architecture.webp)

## The Docker daemon

The Docker daemon (`dockerd`) listens for Docker API requests and manages Docker objects
such as images, containers, networks, and volumes. A daemon can also communicate with
other daemons to manage Docker services.

## The Docker client

The Docker client (`docker`) is the primary way that many Docker users interact with
Docker. When you use commands such as `docker run`, the client sends these commands to
`dockerd`, which carries them out. The `docker` command uses the Docker API. The Docker
client can communicate with more than one daemon.

## Docker Desktop

Docker Desktop is an easy-to-install application for Mac, Windows or Linux environment
that enables you to build and share containerized applications and microservices. Docker
Desktop includes the Docker daemon (`dockerd`), the Docker client (`docker`), Docker
Compose, Docker Content Trust, Kubernetes, and Credential Helper.

## Docker registries

A Docker registry stores Docker images. Docker Hub is a public registry that anyone can
use, and Docker looks for images on Docker Hub by default. You can even run your own
private registry.

When you use `docker pull` or `docker run` commands, Docker pulls the required images
from your configured registry. When you use the `docker push` command, Docker pushes
your image to your configured registry.


