# Docker Compose

Docker Compose is a tool that lets you **define and run multi-container Docker applications** using a single YAML file named `docker-compose.yaml`.

Instead of running multiple `docker run` commands manually, you can describe all your services and their configurations in one place.

---

## Why Use Docker Compose?

- Run multiple containers together (e.g., a web app + a database)
- Define volumes, networks, ports, and environment variables in one file
- Start everything with a single command:  
  ```bash
  docker-compose up
  ```

### Basic Structure

```yaml
version: "3.9"

services:
  service_name:
    image: image_name
    environment:
      - VAR=value
    ports:
      - "host_port:container_port:mode(rw by default)"
    volumes:
      - "./host_path:/container_path"

```

## Basic Docker Commands

| Command                 | What It Does                                      |
|-------------------------|---------------------------------------------------|
| `docker-compose up`     | Starts all services                               |
| `docker-compose up -d`  | Starts in detached (background) mode              |
| `docker-compose down`   | Stops and removes all services, networks, volumes |
| `docker-compose ps`     | Lists running services                            |
| `docker-compose logs`   | Shows logs for all services                       |

## Sample Exercise

Use the `docker-compose.yaml` provided

1. `docker-compose up` in the same dir as docker-compose.yaml

2. Login to pgadmin

3. Register server

4. Check to see ny_taxi database exist

5. `CTRL + C` to stop