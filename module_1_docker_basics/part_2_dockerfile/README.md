# Basic Dockerfile instructions

## `FROM` instruction

- The **first instruction** in every Dockerfile
- Defines the **base image** for your Docker image

### Base Image

- A prebuilt image with an operating system and/or language runtime
- Commonly hosted on [Docker Hub](https://hub.docker.com)
- Examples include:
  - `ubuntu`
  - `python`

### Examples

- Python 3.10
    ```dockerfile
    FROM python:3.10
    ```

- Ubuntu
    ```dockerfile
    FROM ubuntu
    ```

## `RUN` instruction

- The `RUN` instruction is used to execute commands **during the image build process**.
- Common use cases include:
  - Installing packages
  - Creating directories
  - Running scripts

### Example

- Installing CURL on Ubuntu

    ```dockerfile
    FROM ubuntu
    RUN apt update && apt install -y curl
    ```

## `ENTRYPOINT` instruction

- Defines the default command to run when the container starts
- Makes the container behave like an executable
- Arguments passed to `docker run` are passed to the `ENTRYPOINT` command

### Example
- Installs Python and starts the Python interactive console
    ```dockerfile
    FROM python:3.10
    ENTRYPOINT ["python"]
    ```
