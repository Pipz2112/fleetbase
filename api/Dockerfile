FROM php:8.2-fpm-alpine

RUN apk add --no-cache \
    bash git curl zip unzip libpng-dev libjpeg-turbo-dev freetype-dev oniguruma-dev icu-dev libxml2-dev zlib-dev libzip-dev mysql-client nodejs npm

RUN docker-php-ext-install pdo_mysql zip gd intl opcache bcmath

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

WORKDIR /fleetbase/api

EXPOSE 8800

CMD ["php-fpm"]
