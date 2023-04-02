FROM httpd:2-alpine

COPY httpd.conf /usr/local/apache2/conf/httpd.conf

RUN mkdir /usr/local/apache2/htdocs/upload

RUN wget https://github.com/opencart/opencart/releases/download/4.0.1.1/opencart-4.0.1.1.zip 
RUN mv opencart-4.0.1.1.zip /tmp/opencart.zip
RUN unzip /tmp/opencart.zip -d /tmp/ && mv /tmp/upload/* /usr/local/apache2/htdocs/upload/ && rm -rf /tmp/*

#RUN mv /usr/local/apache2/htdocs/upload/config-dist.php /usr/local/apache2/htdocs/upload/config.php 
#RUN mv /usr/local/apache2/htdocs/upload/admin/config-dist.php /usr/local/apache2/htdocs/upload/admin/config.php 
#RUN chmod 0777 /usr/local/apache2/htdocs/upload/config.php
#RUN chmod 0777 /usr/local/apache2/htdocs/upload/admin/config.php


WORKDIR /usr/local/apache2

# /usr/local/apache2/htdocs/

COPY httpd.conf /usr/local/apache2/conf/httpd.conf
