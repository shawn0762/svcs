FROM php:8.1.18-fpm

RUN apt update && apt-get update && apt-get -y install vim \
  && docker-php-ext-configure pdo_mysql -with-php-config=/usr/local/bin/php-config \
    && docker-php-ext-install pdo_mysql

RUN php -r "copy('https://install.phpcomposer.com/installer', 'composer-setup.php');" \
    && php composer-setup.php --2.5.5  \
    && php -r "unlink('composer-setup.php');"  \
    && mv composer.phar /usr/local/bin/composer

#RUN apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng-dev  \
#    && docker-php-ext-configure gd -with-php-config=/usr/local/bin/php-config -with-freetype-dir -with-jpeg-dir -with-png-dir \
#  && docker-php-ext-install gd

#RUN pecl install igbinary-3.2.14
RUN apt-get -y install git
# composer install需要
RUN apt-get -y install libzip-dev \
    && docker-php-ext-install zip

RUN apt-get -y install unzip
COPY php.ini /usr/local/etc/php/php.ini
