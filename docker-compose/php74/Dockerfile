FROM php:7.4-fpm

RUN apt update && apt-get update && apt-get -y install vim

RUN docker-php-ext-configure bcmath -with-php-config=/usr/local/bin/php-config \
    && docker-php-ext-install bcmath \
    && docker-php-ext-configure pdo_mysql -with-php-config=/usr/local/bin/php-config \
    && docker-php-ext-install pdo_mysql \
    && php -r "copy('https://install.phpcomposer.com/installer', 'composer-setup.php');" \
    && php composer-setup.php --2.2 && php -r "unlink('composer-setup.php');" && mv composer.phar /usr/local/bin/composer

RUN pecl install igbinary-3.2.7 \
      # 这里有几个选项可以开启，优化性能
    && pecl install redis-5.3.7

COPY php.ini /usr/local/etc/php/php.ini
