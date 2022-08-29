FROM php:7.4-alpine

RUN sed -i 's@dl-cdn.alpinelinux.org@mirrors.aliyun.com@g' /etc/apk/repositories \
    && apk update \
    && apk add git \
    && apk add wget \
    && apk add vim

RUN cd /opt \ 
    && wget https://mirrors.aliyun.com/composer/composer.phar \
    && chmod +x composer.phar \
    && mv composer.phar /usr/bin/composer \
    && composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/


