FROM php:8.1-fpm-alpine

RUN apk add --no-cache libzip-dev zlib-dev libpng-dev libjpeg-turbo-dev freetype-dev \
	&& docker-php-ext-configure gd --with-freetype --with-jpeg \
	&& docker-php-ext-install -j$(nproc) zip gd mysqli


RUN mkdir -p /usr/local/apache2/htdocs/upload/1

RUN wget https://github.com/opencart/opencart/releases/download/4.0.1.0/opencart-4.0.1.0.zip 
RUN mv opencart-4.0.1.0.zip /tmp/opencart.zip
RUN unzip /tmp/opencart.zip -d /tmp/ && mv /tmp/upload/* /usr/local/apache2/htdocs/upload/ && rm -rf /tmp/*

RUN mv /usr/local/apache2/htdocs/upload/config-dist.php /usr/local/apache2/htdocs/upload/config.php 
RUN mv /usr/local/apache2/htdocs/upload/admin/config-dist.php /usr/local/apache2/htdocs/upload/admin/config.php 
RUN chmod 0777 /usr/local/apache2/htdocs/upload/config.php
RUN chmod 0777 /usr/local/apache2/htdocs/upload/admin/config.php



CMD ["php-fpm"]

EXPOSE 9000
