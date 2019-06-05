FROM php:7.1-fpm

RUN apt-get update
RUN apt-get install -y sudo

RUN curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -

RUN apt-get install -y \
        git \
        unzip \
        libz-dev \
        aptitude \
        libpng-dev \
        mysql-client \
        libmcrypt-dev \
        libmemcached-dev \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        nodejs \
        npm \
 && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
 && docker-php-ext-install -j$(nproc) gd iconv mcrypt pdo_mysql \
 && pecl install xdebug-2.5.5 \
 && pecl install memcached \
 && echo extension=memcached.so >> /usr/local/etc/php/conf.d/memcached.ini



RUN npm cache verify

RUN npm install --cache /tmp/empty-cache

RUN npm install -g npm

RUN npm cache clean --force


RUN npm install n -g \
 && n stable \
 && ln -sf /usr/local/bin/node /usr/bin/node \

# install composer
RUN cd '/' \
 && php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
 && php composer-setup.php \
 && php -r "unlink('composer-setup.php');" \
 && mv composer.phar /usr/local/bin/composer

WORKDIR /var/www
# install vim-gnome
RUN aptitude install -y vim

