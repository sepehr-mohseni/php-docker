FROM php:8.2-fpm-alpine

RUN docker-php-ext-install pdo pdo_mysql 

ENV COMPOSER_ALLOW_SUPERUSER=1

COPY --from=composer:2.5 /usr/bin/composer /usr/bin/composer

COPY ./app/composer.* ./

RUN composer install --prefer-dist --no-dev --no-scripts --no-progress --no-interaction

COPY ./app .

RUN composer dump-autoload --optimize