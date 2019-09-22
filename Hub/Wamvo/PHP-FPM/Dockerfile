FROM php:7.2-fpm

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        git

RUN docker-php-ext-install -j$(nproc) iconv gd zip mysqli mbstring pdo pdo_mysql
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www/html
RUN  chown -R $USER:www-data /var/www/html/
RUN  chmod -R 775 /var/www/html/
EXPOSE 9000
CMD ["php-fpm", "-g", "daemon off;"]