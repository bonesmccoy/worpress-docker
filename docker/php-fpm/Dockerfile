FROM php:5.6-fpm

MAINTAINER Daniele Murroni <daniele.murroni@gmail.com>

RUN apt-get update && apt-get install -y git zlib1g-dev -y libpng12-dev libjpeg-dev vim
RUN pecl install xdebug
RUN docker-php-ext-enable xdebug
RUN docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr
RUN docker-php-ext-install pdo gd mysqli zip

ADD wordpress.ini /usr/local/etc/php/conf.d
ADD xdebug.ini /usr/local/etc/php/conf.d/20-xdebug.ini
ADD php.ini /usr/local/etc/php/conf.d/30-php.ini

ADD wordpress.pool.conf /etc/php5/fpm/pool.d/

RUN usermod -u 1000 www-data

EXPOSE 9000

WORKDIR /var/www
