FROM php:7.4-apache
RUN pecl install --force xdebug && docker-php-ext-enable xdebug
RUN apt-get update && apt-get upgrade -y && apt-get install -y git
RUN apt-get install -y $PHPIZE_DEPS zip unzip libzip-dev libpng-dev sendmail libonig-dev freetds-dev libicu-dev libpq-dev unixodbc-dev
#RUN docker-php-ext-configure pdo_dblib --with-libdir=/lib/x86_64-linux-gnu \
#    && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
#    && docker-php-ext-configure pdo_odbc --with-pdo-odbc=unixODBC,/usr
RUN docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql
RUN docker-php-ext-configure zip
RUN docker-php-ext-install zip gd intl mbstring mysqli pdo pgsql pdo_mysql pdo_pgsql \
    && docker-php-ext-enable mysqli pdo_mysql pdo_pgsql
RUN pecl install -o -f grpc
#install protoc
RUN docker-php-ext-enable grpc
RUN apt install -y nodejs
RUN apt install -y npm
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
#RUN composer self-update --1
#RUN composer global require "fxp/composer-asset-plugin:^1.2.0"
#WORKDIR "/var/www/html/beezpzadmindashboard"
#RUN composer install && npm install
#RUN composer self-update --2
#WORKDIR "/var/www/html/socialyze"
#CMD composer install
#CMD ["sh", "-c", "cd /var/www/html/beezpzadmindashboard; composer install; npm install;composer self-update --2 && cd /var/www/html/socialyze && composer install"]
COPY sites-available/beezpz.conf /etc/apache2/sites-available/beezpz.conf
RUN a2ensite beezpz.conf
RUN a2enmod rewrite
RUN a2enmod headers
RUN a2enmod proxy
RUN a2enmod proxy_http
RUN service apache2 restart