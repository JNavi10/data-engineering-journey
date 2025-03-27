# PostgreSQL

PostgreSQL is a powerful, open-source relational database system.

## How to run postgresql locally within docker

NOTE: The following bash command only sets up PostgreSQL. To interact with it, You need to use another bash terminal to talk to it.

TLDR:
1. Execute the following bash command
2. Open another bash terminal
3. Execute pgcli explained further down

### Bash Command

```bash
docker run \
-e POSTGRES_USER="root" \
-e POSTGRES_PASSWORD="root" \
-e POSTGRES_DB="ny_taxi" \
-v $pwd/ny_taxi_postgres_data:/var/lib/postgresql/data \
-p 5432:5432 \
postgres:13
```

### Command breakdown
```bash
docker run
```
Start a new container from the image I will provide later in the code.

### `-e` (environment variable) option
The -e flag is used to set environment variables inside the container — in this case, for PostgreSQL configuration.

### Docker Command Breakdown

| Part | Description |
|------|-------------|
| `-e POSTGRES_USER="root"` | Sets the database username to `root` inside the container |
| `-e POSTGRES_PASSWORD="root"` | Sets the password for the user `root` |
| `-e POSTGRES_DB="ny_taxi"` | Creates a database named `ny_taxi` |

### -v (volume) option
``` bash
-v $(pwd)/ny_taxi_postgres_data:/var/lib/postgresql/data	
```
Save the database files on your computer, so you don't lose them

Here is a further break down:

| Part |	Meaning |
|------|------------|
| $(pwd)/ny_taxi_postgres_data |	The folder on your computer (host). This is where the database files will be saved. |
| /var/lib/postgresql/data	| The location inside the container where PostgreSQL stores its data. |

So any data the database writes to `/var/lib/postgresql/data` inside the container will be saved to `$(pwd)/ny_taxi_postgres_data` on your machine.

This ensures your data persists even if the container is stopped or deleted.

REMEMBER: Container does not save its state unless you explicitly save it to a volume

### -p (port mapping) option
```bash
-p 5432:5432
```
This connects a port on your computer to a port inside the container, so other tools can talk to the database.

The **first 5432** = your host machine port

The **second 5432** = the PostgreSQL server inside the container

So when you connect to
`
localhost:5432
`
on your host machine

You're talking to PostgreSQL inside the Docker container.

NOTE: Port 5432 is the default port for PostgreSQL.


## pgcli

CLI - Command Line Interface

pgcli is a cli for PostgreSQL

Install it(for now) using
```bash
pip install pgcli
```
in your conda environment.

To run use following bash command

```bash
pgcli -h localhost -p 5432 -u root -d ny_taxi
```

You will be prompted for password. If you remember on the `docker run` command, we set the password to 'root'. Type 'root' and Enter.

You should now see a pgcli prompt

### command breakdown
| Option         | Description                                            |
|----------------|--------------------------------------------------------|
| `pgcli`        | Starts the `pgcli` interactive PostgreSQL client       |
| `-h localhost` | Connects to the database host at `localhost`           |
| `-p 5432`      | Uses port `5432`, the default port for PostgreSQL      |
| `-u root`      | Logs in using the database username `root`             |
| `-d ny_taxi`   | Connects to the database named `ny_taxi`               |

