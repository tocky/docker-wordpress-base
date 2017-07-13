# docker-wordpress-base

This is a base project which WordPress works simply on your local using Docker container.

## Prerequisite

- Docker
- Docker Compose

```
$ docker -v
Docker version 17.06.0-ce, build 02c1d87
$ docker-compose -v
docker-compose version 1.14.0, build c7bdf9e
```

## How it works

### Launch

```
$ git clone https://github.com/tocky/docker-wordpress-base
$ cd docker-wordpress-base
$ cp .env{.example,}
$ docker-compose up -d
```

Then you can start at http://localhost:8000/

### Shutdown

```
$ docker-compose down -v
```

## How to develop

An empty directories (`myplugin` and `mytheme`) is already exist, and these are synched with container. Then you can develop something in these directories.

## What you should know

- After setting WordPress up initially, data will be stored in `data/db` directory on your host computer (yes, this directory is being synched with MySQL container).
- If you need to load initial data, your WordPress data can be saved with `mysqldump` command. Then the dumped file will be imported next time.
    - `docker exec -it mywordpress_db_1 sh -c 'mysqldump wordpress -u wordpress -pwordpress 2> /dev/null' > .data/mysql.dump.sql`
- You can add 3rd-party plugins or themes, add a `RUN` statement in `wordpress/Dockerfile`.
    - [Contact Form 7](https://wordpress.org/plugins/contact-form-7/) has been added.
