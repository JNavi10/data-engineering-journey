# Run Docker Image

## `run` command

- Use the `docker run` command to start a container from a Docker image.
- This creates a **new container** and runs the image's default command.

### Basic Syntax
```bash
docker run image-name
```

### `-it` option

- The `-it` option is commonly used when running containers that require user interaction
- Such as:
    - Shell
    - Python


## Sample Exercise
1. If you haven't already, create docker image `python3.10:pandas` in Module 3

2. Run following command
    ```bash
    docker run -it python3.10:pandas
    ```

