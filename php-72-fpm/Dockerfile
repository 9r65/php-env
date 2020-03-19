FROM php:7.2-fpm-alpine

WORKDIR /var/www/html
EXPOSE 9000

COPY php.ini /usr/local/etc/php/

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories && apk update \
    && apk add alpine-sdk autoconf \
    apache2-dev \
    aspell-dev \
    bison \
    bzip2-dev \
    curl-dev \
    db-dev \
    enchant-dev \
    freetds-dev \
    freetype-dev \
    gdbm-dev \
    gettext-dev \
    gmp-dev \
    icu-dev \
    imap-dev \
    krb5-dev \
    libedit-dev \
    libical-dev \
    libjpeg-turbo-dev \
    libmcrypt-dev \
    libpng-dev \
    libressl-dev \
    libwebp-dev \
    libxml2-dev \
    libxpm-dev \
    libxslt-dev \
    libzip-dev \
    net-snmp-dev \
    openldap-dev \
    pcre-dev \
    postgresql-dev \
    re2c \
    recode-dev \
    sqlite-dev \
    tidyhtml-dev \
    unixodbc-dev \
    zlib-dev \
 && pecl install redis \
 && docker-php-ext-enable redis \
 && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
 && docker-php-ext-install zip \
 && docker-php-ext-install bcmath \
 && docker-php-ext-enable opcache \
 && docker-php-ext-install -j$(nproc) gd \
 && docker-php-ext-install pdo pdo_mysql mysqli \
 && curl -sS https://install.phpcomposer.com/installer | php -- --install-dir=/usr/bin/ --filename=composer \
 && composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/