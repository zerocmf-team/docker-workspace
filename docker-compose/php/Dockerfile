FROM daocloud.io/php:5.6-fpm

RUN sed -i -E 's/(deb|security).debian.org/mirrors.aliyun.com/g' /etc/apt/sources.list

RUN  apt-get update && apt-get install -y \ 
    libfreetype6-dev \ 
    libjpeg62-turbo-dev \ 
    libmcrypt-dev \ 
    libpng-dev \ 
    && docker-php-ext-install -j $(nproc) iconv mcrypt \ 
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \ 
    && docker-php-ext-install -j $(nproc) gd \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install mysqli