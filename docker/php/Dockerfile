ARG PHP_SAPI

FROM php:7.1-${PHP_SAPI}-alpine

ENV PHPIZE_DEPS $PHPIZE_DEPS rabbitmq-c-dev libxml2-dev

RUN apk add --no-cache --virtual .php-rundeps rabbitmq-c && \
    apk fetch -s --no-cache -X http://dl-cdn.alpinelinux.org/alpine/edge/community composer | tail -n +4 | gunzip -f | tar -C / -vx usr/bin/composer && \
    pecl bundle -d /usr/src/php/ext amqp && \
    touch /usr/src/php/.docker-delete-me && \
    docker-php-ext-install bcmath pcntl soap amqp zip phar

WORKDIR /var/www/html
