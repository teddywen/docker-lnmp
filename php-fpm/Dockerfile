######
# See: https://hub.docker.com/_/php/
######

FROM hub.c.163.com/library/php:7.1.0-fpm
LABEL com.candlesgo.image="hub.c.163.com/teddywen/lnmp-fpm:1.0.0" \
      com.candlesgo.author="teddywen" \
      com.candlesgo.email="763323819@qq.com" \
      com.candlesgo.description="This is a fpm image for yii2 and laravel." \
      com.candlesgo.version="1.0.0" \
      com.candlesgo.release-date="2017-05-29"

######
# Change apt sources from debian to netease
# link: http://mirrors.163.com/.help/debian.html
######
COPY ./sources.list /etc/apt/sources.list

######
# You can install php extensions using docker-php-ext-install
######

######
# Core extensions install
######
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
    && docker-php-ext-install -j$(nproc) iconv mcrypt \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

######
# Redis, xdebug and Memcached install
######
RUN pecl install redis-3.1.0 \
    && pecl install xdebug-2.5.0 \
    && docker-php-ext-enable redis xdebug \
    && apt-get update && apt-get install -y \
        libpq-dev \
        libmemcached-dev \
        curl \
    && curl -L -o /tmp/memcached.tar.gz "https://github.com/php-memcached-dev/php-memcached/archive/php7.tar.gz" \
    && mkdir -p /usr/src/php/ext/memcached \
    && tar -C /usr/src/php/ext/memcached -zxvf /tmp/memcached.tar.gz --strip 1 \
    && docker-php-ext-configure memcached \
    && docker-php-ext-install memcached \
    && rm /tmp/memcached.tar.gz \
    && apt-get remove -y curl

######
# Custom extensions install
######
RUN apt-get update && apt-get install -y \
        git \
        openssl \
        libicu-dev \
    && git clone https://github.com/laruence/yaconf.git /usr/src/php/ext/yaconf/ \
    && docker-php-ext-configure intl \
    && docker-php-ext-install -j$(nproc) pdo_mysql mysqli mbstring opcache zip pcntl yaconf intl \
    && apt-get remove -y git
