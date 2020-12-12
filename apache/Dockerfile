FROM httpd:2.4.46-alpine

RUN apk update; \
    apk upgrade;

# Copy Apache virtual host file to proxy php requests to php-fpm container
COPY moodle.conf /usr/local/apache2/conf/moodle.conf
RUN echo "Include /usr/local/apache2/conf/moodle.conf" \
    >> /usr/local/apache2/conf/httpd.conf

# modify www-data user to have id 1000
RUN apk add \
        --no-cache \
        --repository http://dl-3.alpinelinux.org/alpine/edge/community/ --allow-untrusted \
        --virtual .shadow-deps \
        shadow \
    && usermod -u 1000 www-data \
    && groupmod -g 1000 www-data \
    && apk del .shadow-deps
