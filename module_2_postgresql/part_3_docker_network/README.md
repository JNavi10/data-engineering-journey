# Docker Network

A Docker network is a way to let containers talk to each other

## Basic commands

### List networks
```bash
docker network ls
```
### Create a network

```bash
docker network create my-network
```

### Remove a network

```bash
docker network rm my-network
```

## Connecting Postgres container and pgadmin container

- This is for educational purpose only, no one does it this way. So just stick with me.

- It will look complex, but it's mostly code we already covered with few added lines.
We'll cover them later

1. Close previous containers

2. Execute following command

    ```bash
    docker network create pg-network

    docker run \
    -e POSTGRES_USER="root" \
    -e POSTGRES_PASSWORD="root" \
    -e POSTGRES_DB="ny_taxi" \
    -v $pwd/ny_taxi_postgres_data:/var/lib/postgresql/data \
    -p 5432:5432 \
    --network=pg-network \
    --name pg-database \
    postgres:13
    ```

3. Then on separate terminal:
    ```bash
    docker run \
    -e PGADMIN_DEFAULT_EMAIL="admin@admin.com" \
    -e PGADMIN_DEFAULT_PASSWORD="root" \
    -p 8080:80 \
    --network=pg-network \
    --name pgadmin \
    dpage/pgadmin4

    ```

4. Go to `http://localhost:8080` and login

5. Right click 'Servers' -> 'Register' -> 'Server'

    - It may differ from version to version but it should always be in Right clicking 'Servers'
    

6. Name it 'Docker localhost'

7. Go to Connection
    ```
    Host name = pg-database
    Username = root
    Password = root
    ```

    It's everything we set up before

8. Under 'Docker localhost' - 'Databases' 

    You should be able to find ny_taxi

## Import

- Assume we have a import script named "import_data.py"
- We would use following Dockerfile and bash command to import data

```dockerfile
FROM python:3.10

RUN apt-get install wget
RUN pip install pandas sqlalchemy psycopg2

WORKDIR /app
COPY import_data.py import_data.py

ENTRYPOINT [ "python", "import_data.py" ]
```

```bash
docker build -t taxi_import:v01 .

docker run -it taxi_import:v01
```

The important thing to note here is `apt-get`

### `apt-get`

- `apt-get` is a command-line tool used to manage packages, and is a predecessor to `apt`.

### Why use `apt-get` instead of `apt`?

- `apt-get` is more **stable and script-friendly**
- It avoids **interactive prompts and progress bars** — ideal for **Dockerfiles and automation**
