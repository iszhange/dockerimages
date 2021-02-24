FROM php:7.2-fpm
ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/
RUN chmod +x /usr/local/bin/install-php-extensions \
    && sync \
    && install-php-extensions gd mysqli pdo_mysql
COPY php.ini /usr/local/etc/php/php.ini