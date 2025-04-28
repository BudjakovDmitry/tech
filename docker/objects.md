# Docker objects

## Images

Image is a read-only template with instructions for creating a Docker container. Often,
an image is based on another image, with some additional customization.

Yom might create your own images, or you might only use those create by others and
published in a registry. To build your own image, you create a Dockerfile for defining
the steps needed to create the image and run it. Each instruction in a Dockerfile
create a layer in the image. When you change the Dockerfile and rebuild the image, only
those layers which have changed are rebuilt.

## Containers

A container is a runnable instance of an image. You can create, start, stop, move or
delete a container using Docker API or CLI. You can connect a container to one or more
networks, attach storage to it, or even create a new image based in its current state.

By default, a container is relatively well isolated from other containers and its host
machine. You can control how isolated a container's network, storage, or other
underlying subsystems are from other containers or from the host machine.

A container is defined by its image as well as any configuration options you provide to
it when you create or start it. When container is removed, any changes to ots state that
aren't stored in persistent storage dissapear.
