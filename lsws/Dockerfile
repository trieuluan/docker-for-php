FROM litespeedtech/openlitespeed:latest
RUN apt-get update
RUN apt-get install lsphp56 lsphp74 lsphp80 -y
RUN apt-get update
RUN apt-get install lsphp74-* lsphp80-* lsphp56-* make gcc -y
RUN wget http://xdebug.org/files/xdebug-3.1.4.tgz;
RUN tar -xvzf xdebug-3.1.4.tgz
RUN cd xdebug-3.1.4;/usr/local/lsws/lsphp74/bin/phpize;./configure --with-php-config=/usr/local/lsws/lsphp74/bin/php-config;make;cp modules/xdebug.so /usr/local/lsws/lsphp74/lib/php/20190902/xdebug.so
RUN apt-get update
RUN apt-get install autoconf zlib1g-dev -y
RUN apt-get install lsphp74-pear lsphp80-pear lsphp56-pear -y
RUN /usr/local/lsws/lsphp74/bin/pecl install grpc
RUN /usr/local/lsws/lsphp80/bin/pecl install mongodb
RUN /usr/local/lsws/lsphp80/bin/pecl install xdebug
RUN /usr/local/lsws/lsphp56/bin/pecl install xdebug
