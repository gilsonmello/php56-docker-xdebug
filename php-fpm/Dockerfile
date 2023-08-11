FROM php:5.6-fpm-alpine

RUN apk update

# Install dependencies
RUN apk --no-cache add autoconf g++ libtool make pcre-dev \
    icu-dev \
    libxml2-dev \
    sqlite-dev \
    curl-dev \
    libpng-dev \
    libjpeg-turbo-dev \
    libmcrypt-dev \
    git \
    freetype-dev && \
    rm -rf /tmp/* && \
    rm -rf /var/cache/apk/*

RUN docker-php-ext-configure mcrypt

# Install Xdebug from source
RUN git clone -b xdebug_2_5 https://github.com/xdebug/xdebug.git /root/xdebug \
  && cd /root/xdebug && phpize; ./configure --enable-xdebug; make; cp modules/xdebug.so /usr/local/lib/php/extensions/no-debug-non-zts-20131226

RUN docker-php-ext-install zip \
  mcrypt \
  curl \
  tokenizer \
  session \
  ctype \ 
  simplexml \ 
  opcache \ 
  pdo \
  pdo_mysql \
  iconv \
  xml \
  dom \
  mbstring \
  gd \
  intl \
  soap \
  bcmath \
  mysqli

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www/app

CMD ["php-fpm"]