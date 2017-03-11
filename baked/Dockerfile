FROM ubuntu:precise

RUN apt-get update &&\
 apt-get --no-install-recommends -y install \
  apache2 \
  php5 php5-mysql php5-gd \
  unzip wget &&\
 apt-get clean &&\
 rm -rf /var/cache/apt/archives/* /var/lib/apt/lists/*

RUN a2enmod rewrite

ENV VERSION 0.1.4

RUN mkdir /root/temp &&\
 cd /root/temp &&\
 wget http://bakedcms.org/download/download/$VERSION -O baked.zip &&\
 unzip baked.zip &&\
 rm -rf /var/www &&\
 mv baked /var/www &&\
 rm -rf /root/temp

WORKDIR /var/www
RUN chmod 606 my.php &&\
 chmod -R 707 app/tmp app/webroot/files
 
COPY 000-default /etc/apache2/sites-enabled/
COPY apache2-foreground /usr/local/bin

EXPOSE 80
CMD ["apache2-foreground"]

