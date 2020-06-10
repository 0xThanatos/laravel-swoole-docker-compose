FROM php:7.4.6-fpm
WORKDIR "/app"

# Fix debconf warnings upon build
ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update -y && \
    apt-get install git -y

# Install Swoole
RUN cd /tmp && git clone https://github.com/swoole/swoole-src.git && \
    cd swoole-src  && \
    phpize && \
    ./configure && \
    make && make install

# Add swoole extension to php configuration
RUN touch /usr/local/etc/php/conf.d/swoole.ini && \
    echo 'extension=swoole.so' > /usr/local/etc/php/conf.d/swoole.ini

# Install selected extensions and other stuff
RUN apt-get update && \
    apt-get install -y libpq-dev && \
    docker-php-ext-install \
    pdo \
    pdo_pgsql

# Migrate & Start Swoole server
WORKDIR "/app/laravel-swoole-tutorial"
RUN php artisan migrate --force \
    php artisan swoole:http start