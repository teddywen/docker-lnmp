######
# See: https://hub.docker.com/_/memcached/
######

FROM hub.c.163.com/library/memcached:latest
LABEL com.candlesgo.image="hub.c.163.com/teddywen/lnmp-memcached:1.0.0" \
      com.candlesgo.author="teddywen" \
      com.candlesgo.email="763323819@qq.com" \
      com.candlesgo.description="This is a memcached image for yii2 and laravel." \
      com.candlesgo.version="1.0.0" \
      com.candlesgo.release-date="2017-05-29"

######
# Change apt sources from debian to netease
# link: http://mirrors.163.com/.help/debian.html
######
COPY ./sources.list /etc/apt/sources.list
