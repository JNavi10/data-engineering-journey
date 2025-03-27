# Building Docker Image

## `build` Command

- Use the `docker build` command to create a Docker image from a Dockerfile.
- This command reads the Dockerfile and packages everything into an image.

### Most basic syntax

- You can simply provide the directory where Dockerfile is located

```bash
docker build .
```
- ⚠️ **Not recommended**, educational purpose only
- Always include -t option explained below


### `-t` option

- The `-t` flag stands for **tag**, and it's recommended to always use it.
- It lets you give your image a name
    ```bash
    docker build -t name .
    ```
- Optionally tags can be provided in following syntax
    ```bash
    docker build -t name:tag .
    ```

### tag

- A **tag** is used to mark image versions (e.g., `v1`, `dev`, `latest`)
- If no tag is specified, Docker uses `latest` by default

### Example

```bash
docker build -t myapp:1.0 .
```

## Sample Exercise
1. 
    Make a Dockerfile by copy pasting the code below
    ```dockerfile
    FROM python:3.10
    RUN pip install pandas
    ENTRYPOINT ["python"]
    ```

    OR

    Use the Dockerfile provided in this module


2. Build a Docker Image 
    ```bash
    docker build -t python3.10:pandas .
    ```

3. Check if image is there
    ```bash
    docker images python3.10:pandas
    ```
    You should see something like this
    ```
    REPOSITORY   TAG       IMAGE ID       CREATED              SIZE
    python3.10   pandas    e7368f373a0e   About a minute ago   1.71GB
    ```
