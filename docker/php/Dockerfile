FROM php:8.2-fpm-alpine

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
    apk add --update linux-headers && \
    apk add --no-cache --virtual deps pcre-dev ${PHPIZE_DEPS} && \
    pecl install redis xdebug && \
    docker-php-ext-enable redis xdebug && \
    docker-php-ext-install pdo_mysql sockets && \
    apk del deps && \
    apk add --no-cache git
RUN apk add --no-cache bash && \
    curl -1sLf 'https://dl.cloudsmith.io/public/symfony/stable/setup.alpine.sh' | bash && \
    apk add symfony-cli