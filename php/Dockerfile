FROM php:7.2-fpm-alpine

RUN apk add --no-cache libpng-dev curl-dev libxml2-dev imap-dev libldap openldap-dev

# RUN docker-php-ext-configure imap --with-kerberos --with-imap-ssl
RUN docker-php-ext-install gd zip curl mbstring soap xml json mysqli pdo pdo_mysql xmlrpc imap ldap session simplexml opcache

# Install APCu extension
ADD https://pecl.php.net/get/apcu-5.1.12.tgz /tmp/apcu.tar.gz
RUN mkdir -p /usr/src/php/ext/apcu\
  && tar xf /tmp/apcu.tar.gz -C /usr/src/php/ext/apcu --strip-components=1

# configure and install
RUN docker-php-ext-configure apcu\
    && docker-php-ext-install apcu

EXPOSE 9000
CMD ["php-fpm"]