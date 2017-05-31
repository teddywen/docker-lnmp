# Forked

Forked from [micooz/docker-lnmp](https://github.com/micooz/docker-lnmp)

# Introduction

Deploy enhanced lnmp(Linux, Nginx, MySQL, PHP7, MEMCACHED, REDIS) using docker for your development.

### Docker Image

Using daocloud mirror as base docker image.

- [daocloud.io/nginx:latest](https://hub.docker.com/_/nginx/)
- [daocloud.io/php:7.0.5-fpm](https://hub.docker.com/_/php/)
- [daocloud.io/mysql:latest](https://hub.docker.com/_/mysql/)
- [daocloud.io/memcached:latest](https://hub.docker.com/_/memcached/)
- [daocloud.io/redis:latest](https://hub.docker.com/_/redis/)

### Architecture

![architecture][1]

The whole app is divided into five Containers:

1. Nginx is running in `Nginx` Container, which handles requests and makes responses.
2. PHP or PHP-FPM is put in `PHP-FPM` Container, it retrieves php scripts from host, interprets, executes then responses to Nginx. It installed extensions yii and laravel needs. If necessary, it will connect to `MySQL` as well.
3. MySQL lies in `MySQL` Container, 
4. Memcached for web cache.
5. Redis for web k-v database.

Our app scripts are located on host, you can edit files directly without rebuilding/restarting whole images/containers.

### Build and Run

At first, you should have had [Docker](https://docs.docker.com) and [Docker Compose](https://docs.docker.com/compose) installed.

Without building images one by one, you can make use of `docker-compose` and simply issue:

    $ sudo docker-compose up

For more operations to containers, please refer to:

    $ sudo docker-compose --help

Check out your https://\<docker-host\> and have fun :beer:

### Contributors

Micooz <micooz@hotmail.com>

sndnvaps <sndnvaps@gmail.com>

### License

MIT

  [1]: architecture.png
