FROM chriswayg/concrete5.7

ENV CONCRETE5_VERSION 5.6.3.4
ENV C5_URL https://www.concrete5.org/download_file/-/view/82244
ENV C5_MD5 f0f0bdccc19e63f8ef2488d7a642fb6f

RUN cd /usr/local/src &&\
 wget --no-verbose $C5_URL -O concrete5.zip &&\
 echo "$C5_MD5  concrete5.zip" | md5sum -c - &&\
 unzip -qq concrete5.zip && \
 rm -v concrete5.zip

COPY docker-entrypoint /docker-entrypoint

