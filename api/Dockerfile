FROM php:8.2-fpm-alpine

# Install dependencies
RUN apk add --no-cache \
    bash git curl zip unzip libpng-dev libjpeg-turbo-dev freetype-dev oniguruma-dev icu-dev libxml2-dev zlib-dev libzip-dev mysql-client nodejs npm

RUN docker-php-ext-install pdo_mysql zip gd intl opcache bcmath

# Copy composer binary from official image
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Set working directory
WORKDIR /fleetbase/api

# Copy application files into container
COPY . .

# Expose port (for php artisan serve or php-fpm)
EXPOSE 8800

# Default command to run php-fpm
CMD ["php-fpm"]
