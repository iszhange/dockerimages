FROM php:7.3-fpm

ARG PROTOBUF_VERSION=21.12

RUN sed -i 's/deb.debian.org/mirrors.163.com/g' /etc/apt/sources.list

RUN apt-get update
RUN apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libzip-dev \
    libmcrypt-dev \
    build-essential \
	openssl \
	libssl-dev \
	wget \
	unzip \
	zip \
    libtool

RUN docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install zip \
    && docker-php-ext-install pcntl \
    && docker-php-ext-install bcmath \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install opcache

RUN pecl install redis-4.0.1 mcrypt-1.0.3 mongodb xlswriter protobuf \
    && docker-php-ext-enable redis mcrypt mongodb xlswriter protobuf

# install protobuf
ADD https://github.com/protocolbuffers/protobuf/releases/download/v${PROTOBUF_VERSION}/protoc-${PROTOBUF_VERSION}-linux-x86_64.zip /opt
RUN cd /opt \
    && unzip protoc-${PROTOBUF_VERSION}-linux-x86_64.zip -d /usr/local/protoc/ \
    && ln -s /usr/local/protoc/bin/protoc /usr/local/bin/protoc \
    && rm protoc-${PROTOBUF_VERSION}-linux-x86_64.zip

# install composer
RUN cd /opt \
    && wget https://mirrors.aliyun.com/composer/composer.phar \
    && chmod +x composer.phar \
    && mv composer.phar /usr/bin/composer \
    && composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/

