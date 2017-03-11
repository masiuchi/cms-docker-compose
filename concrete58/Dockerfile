FROM chriswayg/concrete5.7

ENV CONCRETE5_VERSION 5-8.1.0
ENV C5_URL https://www.concrete5.org/download_file/-/view/93797/
ENV C5_MD5 c78361dc5f71f6a8eebc2de4678dc40f

RUN cd /usr/local/src &&\
 wget --no-verbose $C5_URL -O concrete5.zip &&\
 echo "$C5_MD5  concrete5.zip" | md5sum -c - &&\
 unzip -qq concrete5.zip && \
 rm -v concrete5.zip

