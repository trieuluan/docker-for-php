FROM php:5.6-apache
RUN pecl install --force xdebug-2.5.5 && docker-php-ext-enable xdebug
RUN apt-get update && apt-get upgrade -y && apt-get install -y git
RUN apt-get install -y $PHPIZE_DEPS zip unzip libzip-dev libpng-dev sendmail libonig-dev freetds-dev libicu-dev libpq-dev unixodbc-dev
RUN docker-php-ext-configure zip
RUN docker-php-ext-install zip gd intl mbstring mysqli pdo pgsql pdo_mysql pdo_pgsql \
    && docker-php-ext-enable mysqli pdo_mysql pdo_pgsql
RUN apt install -y nodejs
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
COPY sites-available/lacthai.conf /etc/apache2/sites-available/lacthai.conf
RUN a2ensite lacthai.conf
RUN a2enmod rewrite
RUN a2enmod headers
RUN service apache2 restart