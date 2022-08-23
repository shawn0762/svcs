FROM php:5.6-fpm

RUN apt update && apt-get update && apt-get -y install vim \
  && docker-php-ext-configure pdo_mysql -with-php-config=/usr/local/bin/php-config \
    && docker-php-ext-install pdo_mysql \
    && apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng-dev

RUN docker-php-ext-configure gd -with-php-config=/usr/local/bin/php-config -with-freetype-dir -with-jpeg-dir -with-png-dir \
  && docker-php-ext-install gd

RUN pecl install igbinary-2.0.8 redis-3.1.6

COPY php.ini /usr/local/etc/php/php.ini
