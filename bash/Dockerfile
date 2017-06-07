######
# See: https://hub.docker.com/_/php/
######

FROM hub.c.163.com/library/php:7.1.0
LABEL com.candlesgo.image="hub.c.163.com/teddywen/lnmp-bash:1.0.0" \
      com.candlesgo.author="teddywen" \
      com.candlesgo.email="763323819@qq.com" \
      com.candlesgo.description="This is a bash image for yii2 and laravel." \
      com.candlesgo.version="1.0.0" \
      com.candlesgo.release-date="2017-05-29"

######
# Change apt sources from debian to netease
# link: http://mirrors.163.com/.help/debian.html
######
COPY ./sources.list /etc/apt/sources.list

######
# Custom extensions install
######
RUN apt-get update && apt-get install -y \
        zlib1g-dev \
      && docker-php-ext-install -j$(nproc) zip

######
# Php composer install
######
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php -r "if (hash_file('SHA384', 'composer-setup.php') === '669656bab3166a7aff8a7506b8cb2d1c292f042046c5a994c43155c0be6190fa0355160742ab2e1c88d40d5be660b410') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
    && php composer-setup.php --install-dir=/usr/local/bin --filename=composer \
    && php -r "unlink('composer-setup.php');" \
    && composer config -g repo.packagist composer https://packagist.phpcomposer.com

######
# Node & NPM install
######
RUN apt-get update && apt-get install -y \
        curl \
        wget \
    && curl -sL https://deb.nodesource.com/setup_6.x | bash - \
    && apt-get install -y \
        nodejs \
        build-essential \
    && apt-get remove -y \
        curl \
        wget \
    && npm install yarn -g --registry=https://registry.npm.taobao.org \
    && yarn config set registry https://registry.npm.taobao.org

######
# Tools install
######
RUN apt-get update && apt-get install -y \
        dnsutils \
        traceroute \
        unzip \
        wget \
        curl \
        git \
        less \
        vim
