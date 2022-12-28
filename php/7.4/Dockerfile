FROM php:7.4-alpine

# 支持使用中文
ENV LANG=zh_CN.UTF-8
ENV LANGUAGE=zh_CN.UTF-8

RUN sed -i 's@dl-cdn.alpinelinux.org@mirrors.aliyun.com@g' /etc/apk/repositories;

RUN apk update

# 设置时区
RUN apk add tzdata \
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    && apk del tzdata

RUN apk add wget \
    git \
    vim \
    autoconf \
    gcc \
    g++ \
    make \
    cmake \
    gfortran \
    libffi-dev \
    openssl-dev \
    libtool \
    make \
    make \
    make \
	unzip \
	zip

RUN pecl install ds \
    && docker-php-ext-enable ds

# 安装composer
RUN cd /opt \
    && wget https://mirrors.aliyun.com/composer/composer.phar \
    && chmod +x composer.phar \
    && mv composer.phar /usr/bin/composer \
    && composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/
