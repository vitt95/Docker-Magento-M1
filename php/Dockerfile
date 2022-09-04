FROM arm64v8/php:7.4-fpm-buster

RUN apt-get update && \ 
    apt-get install -y libc-client-dev libkrb5-dev libjpeg62-turbo-dev libfreetype6-dev libxslt-dev zlib1g-dev libpng-dev libzip-dev libxml2-dev libicu-dev libldap2-dev libmagickwand-dev --no-install-recommends && \
    rm -rf /var/lib/apt/lists/* && \
    docker-php-ext-configure imap --with-kerberos --with-imap-ssl && docker-php-ext-install imap && \
    docker-php-ext-install sockets pdo_mysql xsl zip soap intl bcmath exif ldap opcache && \
    docker-php-ext-configure gd --with-jpeg --with-freetype
    RUN docker-php-ext-install gd 

COPY ./config/php.ini $PHP_INI_DIR/conf.d
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN apt-get update && \
    apt-get install -y zip unzip nodejs npm yarn

WORKDIR /var/www/html

EXPOSE 9000