# Deployment

Deployment is at the moment only available via Docker.

Below is a basic Docker Compose setup that can be followed.&#x20;

This will deploy a Postgres Database, Guardlight Server, Guardlight Console and a basic parser and analyzer. If you want more parsers or analyzers, please read [Extending Guardlight](https://refactored.gitbook.io/guardlight/getting-started/extending-guardlight).

An external Postgres database is required.

## Docker Compose

```yaml
services:
    database:
        image: postgres
        ports:
            - 5432:5432
        environment:
            - POSTGRES_USER=guardlight
            - POSTGRES_PASSWORD=securePassword
            - POSTGRES_DATABASE=guardlight

    server:
        image: ghcr.io/guardlight/server
        ports:
            - 6842:6842
        entrypoint:
            - GUARDLIGHT_CORS_ORIGIN=http://<CONSOLE_IP>:<CONSOLE_PORT>
            - GUARDLIGHT_DOMAIN=<SERVER_IP>
            - GUARDLIGHT_DATABASE_USER=guardlight
            - GUARDLIGHT_DATABASE_PASSWORD=securePassword
            - GUARDLIGHT_DATABASE_NAME=guardlight
            - GUARDLIGHT_DATABASE_SERVER=database # Docker Compose Internal IP
            - GUARDLIGHT_DATABASE_PORT=5432

        depends_on:
            - database

    console:
        image: ghcr.io/guardlight/console
        environment:
            - GL_SERVER_URL=<SERVER_IP>:<SERVER_PORT>
        depends_on:
            - server

```

