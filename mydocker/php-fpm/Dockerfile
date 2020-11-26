FROM php:7.4-fpm
WORKDIR "/app"

# Fix debconf warnings upon build
ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update -y && \
    apt-get install git -y

# Install selected extensions
RUN apt-get update && \
    apt-get install -y libpq-dev

RUN pecl install swoole

RUN docker-php-ext-enable swoole

RUN docker-php-ext-install \
    pdo \
    pdo_pgsql
