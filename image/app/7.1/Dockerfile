FROM php:7.1-fpm

RUN apt-get update -y && apt-get install -y git curl libz-dev libmemcached-dev libcurl4-openssl-dev libxml2-dev libssl-dev libpng-dev libonig-dev libpq-dev

# Xdebug
RUN pecl install xdebug-2.9.7 && docker-php-ext-enable xdebug

# Redis
RUN pecl install redis  && docker-php-ext-enable redis

# Memcached
RUN pecl install memcached && docker-php-ext-enable memcached

# MySQL
RUN docker-php-ext-install mysqli

# PostgreSQL
RUN docker-php-ext-install pgsql

#GD
RUN docker-php-ext-install gd

# Composer
RUN curl -sS https://getcomposer.org/installer | php -- \
        --filename=composer \
        --install-dir=/usr/local/bin && \
        echo "alias composer='composer'" >> /root/.bashrc

CMD ["php-fpm", "-F"]

WORKDIR /var/www

EXPOSE 9000