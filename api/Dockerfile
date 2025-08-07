FROM php:8.2-fpm-alpine

# Install dependencies
RUN apk add --no-cache \
    bash git curl zip unzip libpng-dev libjpeg-turbo-dev freetype-dev oniguruma-dev icu-dev libxml2-dev zlib-dev libzip-dev mysql-client nodejs npm $PHPIZE_DEPS

RUN pecl install redis \
    && docker-php-ext-enable redis

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
