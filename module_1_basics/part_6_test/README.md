# Test

- This test will help you refresh your memory of Docker basics

## 1. Terminology

<details>
<summary>1. What is Docker?</summary>
Docker is a tool that lets you run apps in lightweight, portable containers that work the same everywhere.
</details>

<details>
<summary>2. What is Dockerfile?</summary>
Dockerfile is a file that contains all necessary commands to build a Docker Image
</details>

<details>
<summary>3. What is a Docker Image?</summary>
A Docker image is a snapshot of an app and its environment, used to create containers
</details>

<details>
<summary>4. What is a Docker Container?</summary>
A Docker container is a running instance of a Docker Image
</details>

## 2. Dockerfile

<details>
<summary>1. How do you specify Ubuntu as the base image in a Dockerfile?</summary>

```dockerfile
FROM ubuntu
```
</details>

<details>
<summary>2. How do you update and upgrade APT packages in a Dockerfile?</summary>

```dockerfile
RUN apt update && apt upgrade -y
```

**NOTE**: When a Dockerfile runs RUN instructions, they are executed as the root user by default
</details>

<details>
<summary>3. How do you automatically run <code>python</code> when the container starts?</summary>

```dockerfile
ENTRYPOINT ["python"]
```

**NOTE**: You can also use CMD ["python"], which is easier to override.

- `ENTRYPOINT` runs the command every time, and arguments are added to it.
- `CMD` sets a default command, but it can be completely replaced when running the container.
</details>

## 3. Build Image

<details>
<summary>1. Build a Docker Image in current dir with name of <code>test</code> and tag of <code>v1</code></summary>

```bash
docker build -t test:v1 .
```
</details>

## 4. Run Container

<details>
<summary>1. How do you run a container from <code>test:v1</code> in interactive mode?</summary>

```bash
docker run -it test:v1
```
</details>

## 5. Running python script

<details>
<summary>3. How do you set the working directory inside the Docker image?</summary>

```dockerfile
WORKDIR /app
```
</details>

<details> <summary>4. How do you copy <code>sample.py</code> from your local machine into the Docker image?</summary>

```dockerfile
COPY sample.py .
```
</details>

<details> <summary>5. How do you run <code>sample.py</code> using Python when the container starts?</summary>

```dockerfile
ENTRYPOINT ["python", "sample.py"]
```
</details>
