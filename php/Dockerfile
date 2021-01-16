FROM php:7.3-fpm-alpine

RUN apk update; \
    apk upgrade;

ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN apk add --no-cache \
    git \
    postgresql-client \
    msmtp

# Install all PHP extensions required by Moodle
RUN chmod +x /usr/local/bin/install-php-extensions && sync \
    && install-php-extensions \
    bz2 \
    calendar \
    # ctype \
    # curl \
    # dom \
    exif \
    # fileinfo \
    # filter \
    # ftp \
    gd \
    gettext \
    gmp \
    # hash \
    # iconv \
    # json \
    intl \
    # mbstring \
    mysqli \
    opcache \
    # openssl \
    # pcre \
    pdo_mysql \
    pdo_pgsql \
    pgsql \
    shmop \
    soap \
    sockets \
    # sodium \
    # simplexml \
    # spl \
    # tokenizer \
    # xml \
    xmlrpc \
    zip
    # zlib

COPY php.ini $PHP_INI_DIR/php.ini

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && rm -rf /tmp/*

# modify www-data user to have id 1000
RUN apk add \
        --no-cache \
        --repository http://dl-3.alpinelinux.org/alpine/edge/community/ --allow-untrusted \
        --virtual .shadow-deps \
        shadow \
    && usermod -u 1000 www-data \
    && groupmod -g 1000 www-data \
    && apk del .shadow-deps
