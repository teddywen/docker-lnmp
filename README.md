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

1. Nginx is running in `lnmp-nginx` Container, which handles requests and makes responses.
2. PHP or PHP-FPM is put in `lnmp-fpm` Container, it retrieves php scripts from host, interprets, executes then responses to Nginx. It installed extensions yii and laravel needs. If necessary, it will connect to `MySQL` as well.
3. MySQL lies in `lnmp-mysql` Container, 
4. Memcached for web cache lies in `lnmp-memcached` Container.
5. Redis for web k-v database lies in `lnmp-redis` Container.

Our app scripts are located on host, you can edit files directly without rebuilding/restarting whole images/containers.

### Configure

* Setup [php-development.ini](php-fpm/php-development.ini) if necessary.

```ini
[yaconf]
; Set your yaconf dir.
; yaconf.directory=/usr/share/nginx/html/intv/yaconfini
```

```ini
[xdebug]
; host is your local machine's ip
xdebug.remote_host = 192.168.8.154
xdebug.remote_port = 9000
; Set log if necessary。
; xdebug.remote_log = /tmp/xdebug_remote.log
```

* Setup [docker-compose.yml](docker-compose.yml), mount your website dir on the nginx and fpm container.

```yml
nginx:
  volumes:
    # Mount www here.
    - ./app/src:/usr/share/nginx/html
fpm:
  volumes:
    # Mount www here.
    - ./app/src:/usr/share/nginx/html
```

* Add nginx conf file of your website into [nginx/conf.d/](nginx/conf.d/), you may refer to [nginx/conf.d/default.conf.sample](nginx/conf.d/default.conf.sample).


### Build and Run

At first, you should have had [Docker](https://docs.docker.com) and [Docker Compose](https://docs.docker.com/compose) installed.

Without building images one by one, you can make use of `docker-compose` and simply issue:

    $ sudo docker-compose up

Or:

    $ sudo docker-compose up -d

For more operations to containers, please refer to:

    $ sudo docker-compose --help

Check out your http://localhost and have fun :beer:

### Contributors

teddywen <763323819@qq.com>

### License

MIT

  [1]: architecture.png
