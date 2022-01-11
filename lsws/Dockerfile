FROM litespeedtech/openlitespeed:1.7.14-lsphp74
RUN apt-get update
RUN apt-get install lsphp74-* make gcc -y
RUN wget http://xdebug.org/files/xdebug-3.1.2.tgz;
RUN tar -xvzf xdebug-3.1.2.tgz
RUN cd xdebug-3.1.2;/usr/local/lsws/lsphp74/bin/phpize;./configure --with-php-config=/usr/local/lsws/lsphp74/bin/php-config;make;cp modules/xdebug.so /usr/local/lsws/lsphp74/lib/php/20190902/xdebug.so
RUN apt-get install autoconf zlib1g-dev -y
RUN apt-get install lsphp74-pear -y
RUN /usr/local/lsws/lsphp74/bin/pecl install grpc
