FROM php:7.0-apache

RUN apt-get update &&\
 apt-get --no-install-recommends -y install \
  libfreetype6-dev \
  libjpeg62-turbo-dev \
  libpng12-dev \
  unzip \
  wget &&\
 apt-get clean &&\
 rm -rf /var/cache/apt/archives/* /var/lib/apt/lists/*

RUN docker-php-ext-install gd pdo_mysql &&\
 a2enmod rewrite

ENV VERSION 4.0.2.1

RUN cd /root &&\
 wget http://basercms.net/packages/download/basercms/$VERSION -O basercms.zip &&\
 unzip basercms.zip &&\
 rm -rf /var/www/html &&\
 mv basercms /var/www/html &&\
 perl -i -0pe 's/^#//m' /var/www/html/.htaccess &&\
 rm basercms.zip

WORKDIR /var/www/html
RUN chmod 777 \
 app/Config \
 app/Plugin \
 app/tmp \
 app/View/Pages \
 app/db \
 files \
 theme \
 img \
 css \
 js
 
COPY apache2.conf /etc/apache2/

