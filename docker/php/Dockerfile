FROM php:7.4-fpm-alpine

# timezone
ARG TZ

# composer
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer

RUN set -eux && \
  apk update && \
  apk add --update --no-cache --virtual=.build-dependencies \
    autoconf \
    gcc \
    g++ \
    make \
    tzdata && \
  apk add --update --no-cache \
    icu-dev \
    sqlite \
    openssh \
    oniguruma-dev \
    freetype-dev \
    libjpeg-turbo-dev \
    libpng-dev \
    libzip-dev && \
  cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime && \
  echo ${TZ} > /etc/timezone && \
  # pecl install xdebug && \
  docker-php-ext-configure gd --with-freetype=/usr/include --with-jpeg=/usr/include && \
  docker-php-ext-install intl pdo_mysql mbstring zip bcmath gd && \
  # docker-php-ext-enable xdebug && \
  curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer && \
  apk del .build-dependencies
