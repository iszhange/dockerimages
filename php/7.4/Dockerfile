FROM php:7.4-alpine

RUN sed -i 's@dl-cdn.alpinelinux.org@mirrors.aliyun.com@g' /etc/apk/repositories \
    && apk update \
    && apk add git \
    && apk add wget \
    && apk add vim \
    && apk add autoconf \
    && apk add gcc \
    && apk add g++ \
    && apk add make \
    && apk add cmake \
    && apk add gfortran \
    && apk add libffi-dev \
    && apk add openssl-dev \
    && apk add libtool \
    && pecl install ds \
    && docker-php-ext-enable ds # pecl安装的扩展都需要手动启用

RUN cd /opt \ 
    && wget https://mirrors.aliyun.com/composer/composer.phar \
    && chmod +x composer.phar \
    && mv composer.phar /usr/bin/composer \
    && composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/


