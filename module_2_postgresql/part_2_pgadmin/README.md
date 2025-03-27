# pgAdmin

pgAdmin is a free, graphical user interface (GUI) tool for managing PostgreSQL databases.  
It lets you create, browse, query, and manage databases through an easy-to-use visual interface.

## pgAdmin for docker

```bash
docker run \
-e PGADMIN_DEFAULT_EMAIL="admin@admin.com" \
-e PGADMIN_DEFAULT_PASSWORD="root" \
-p 8080:80 \
dpage/pgadmin4
```

### code breakdown

| Option | Description |
|--------|-------------|
| `-e PGADMIN_DEFAULT_EMAIL="admin@admin.com"` | Sets the login email for pgAdmin |
| `-e PGADMIN_DEFAULT_PASSWORD="root"` | Sets the password for that login |
| `-p 8080:80` | Maps port `80` inside the container (pgAdmin’s default) to port `8080` on your host machine |
| `dpage/pgadmin4` | The official Docker image for pgAdmin 4 |

Port mapping can be tricky. For now stick with:
- The container follows web app conventions → serve on port 80
- Port 8080 is a safe, unprivileged port commonly used for web apps during development.


## Accessing pgadmin

Once you've run the code, we need to access it.

1. Open new private window
2. Go to `http://localhost:8080`
3. Login using the credentials we defined above. Which is:
    ```
    Email Address: admin@admin.com
    Password: root
    ```

## Few VERY IMPORTANT things to note

- For now you see nothing in Servers because in this container, only pgAdmin is installed. PostgreSQL is not in the container.
- The reason for opening new private window is because of cache. More often than not previous connections will be cached and cause problems.
