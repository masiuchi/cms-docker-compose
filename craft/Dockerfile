FROM php:7-apache

RUN apt-get update &&\
 apt-get --no-install-recommends -y install \
  libfreetype6-dev \
  libjpeg62-turbo-dev \
  libmcrypt-dev \
  libpng12-dev \
  zlib1g-dev \
  zip unzip wget &&\
 apt-get clean &&\
 rm -rf /var/cache/apt/archives/* /var/lib/apt/lists/*

RUN docker-php-ext-install gd mbstring mcrypt mysqli pdo_mysql zip &&\
 a2enmod rewrite

COPY apache2.conf /etc/apache2/

WORKDIR /root
COPY craft.zip .
RUN unzip craft.zip -d craft &&\
 cp -r craft/public/* /var/www/html/ &&\
 mv /var/www/html/htaccess /var/www/html/.htaccess &&\
 mv craft/craft /var/www/ &&\
 chmod 777 /var/www/craft/app &&\
 chmod 777 /var/www/craft/config &&\
 chmod 777 /var/www/craft/storage

RUN perl -i -0pe "s/'server' => 'localhost'/'server' => 'mysql'/m" /var/www/craft/config/db.php &&\
 perl -i -0pe "s/'database' => ''/'database' => 'craft'/m" /var/www/craft/config/db.php


