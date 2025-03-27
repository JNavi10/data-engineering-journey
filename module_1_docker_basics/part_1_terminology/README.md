# Basic Docker Terminology

## Docker
Docker is a tool that lets you run apps in lightweight, portable containers that work the same everywhere.

## Dockerfile

- **Dockerfile** contains all necessary commands to build a Docker Image
- Think of it as a recipe for building Docker Image
- It's file name is `Dockerfile` with no extension

## Docker Image

- A **Docker image** is a snapshot of an application and its environment.
- Think of it like a **save state in a video game**: everything is preserved exactly as it was.
- You **cannot change** a Docker image once it's created (it's immutable).
- To make changes, you create a **new image** (usually by editing the Dockerfile and rebuilding).

## Docker Container

- A **Docker container** is a **running instance** of a Docker image.
- While a Docker image is like a save file, a container is like **loading that save and playing the game**.
- Multiple containers can be created from the same image, each isolated from the others.

## Relation
- You **build** Docker Image from a Dockerfile
- You **run** Docker Container from a Docker Image
- To put it simply:
    
    📝 Dockerfile 

    ⬇️ build

    📦 Docker Image 

    ⬇️ run
    
    🚀 Docker Container

