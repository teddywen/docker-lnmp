######
# See: https://hub.docker.com/_/redis/
######

FROM daocloud.io/redis:latest
LABEL com.candlesgo.image="teddywen/redis:1.0.0" \
      com.candlesgo.author="teddywen" \
      com.candlesgo.email="763323819@qq.com" \
      com.candlesgo.description="This is a redis image for yii2 and laravel." \
      com.candlesgo.version="1.0.0" \
      com.candlesgo.release-date="2017-05-29"

######
# Change apt sources from debian to netease
# link: http://mirrors.163.com/.help/debian.html
######
COPY ./sources.list /etc/apt/sources.list
