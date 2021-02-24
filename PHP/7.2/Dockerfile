FROM php:7.2-alpine
ENV WORK_DIR /data/www
RUN mkdir -p $WORK_DIR \
    && php -r "copy('https://install.phpcomposer.com/installer', 'composer-setup.php');" \
    && php composer-setup.php \
    && php -r "unlink('composer-setup.php');" \
    && mv composer.phar /usr/local/bin/composer
WORKDIR $WORK_DIR
