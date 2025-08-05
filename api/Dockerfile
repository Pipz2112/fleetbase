FROM php:8.2-fpm-alpine

RUN apk add --no-cache \
    bash git curl zip unzip libpng-dev libjpeg-turbo-dev freetype-dev oniguruma-dev icu-dev libxml2-dev zlib-dev libzip-dev mysql-client nodejs npm

RUN docker-php-ext-install pdo_mysql zip gd intl opcache

# Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

WORKDIR /fleetbase/api
COPY . .

RUN composer install --no-dev --optimize-autoloader

RUN chown -R www-data:www-data /fleetbase/api

EXPOSE 9000
CMD ["php-fpm"]
