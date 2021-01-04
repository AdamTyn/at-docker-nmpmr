FROM php:7.4.13-fpm

COPY resource /home/resource

ARG CHANGE_SOURCE=false

ARG TIME_ZONE=UTC

ENV TIME_ZONE=${TIME_ZONE}

ENV CHANGE_SOURCE=${CHANGE_SOURCE}

ENV LC_ALL=C.UTF-8

RUN ln -snf /usr/share/zoneinfo/$TIME_ZONE /etc/localtime ; \
  echo $TIME_ZONE > /etc/timezone ;
  
RUN mv /home/resource/phpunit-9.3.9.phar /usr/local/bin/phpunit ; \
  chmod 755 /usr/local/bin/phpunit ;

RUN mv /home/resource/composer-2.0.8.phar /usr/local/bin/composer ; \
  chmod 755 /usr/local/bin/composer ; \
  \
  rm -rf /etc/apt/sources.list.d/buster.list ; \
  if [ $CHANGE_SOURCE = true ] ; then \
  mv /etc/apt/sources.list /etc/apt/source.list.bak ; \
  mv /home/resource/163.list /etc/apt/sources.list ; \
  composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/ ; \
  fi ;

RUN apt-get clean \
  && apt-get update --fix-missing ;

RUN apt-get install -y --allow-remove-essential --no-install-recommends libmagickwand-dev \
  procps \
  git \
  zip \
  unzip \
  libtool \
  libzip-dev \
  libtinfo5 \
  libpq-dev \
  libpng-dev \
  libjpeg-dev \
  libwebp-dev \
  libfreetype6-dev \
  libmcrypt-dev \
  libbz2-dev \
  libmhash-dev ;

RUN docker-php-ext-configure gd \
  --with-webp=/usr/include/webp \
  --with-jpeg=/usr/include \
  --with-freetype=/usr/include/freetype2 ;

RUN docker-php-ext-install -j$(nproc) gd pdo_mysql mysqli soap pcntl bcmath bz2 sockets; \
  pecl install /home/resource/imagick-3.4.4.tgz && docker-php-ext-enable imagick ; \
  pecl install /home/resource/xdebug-3.0.1.tgz && docker-php-ext-enable xdebug ; \
  pecl install /home/resource/redis-5.3.2.tgz && docker-php-ext-enable redis ; \
  pecl install /home/resource/swoole-4.5.10.tgz && docker-php-ext-enable swoole ; \
  pecl install /home/resource/mcrypt-1.0.4.tgz && docker-php-ext-enable mcrypt ; \
  pecl install /home/resource/mongodb-1.9.0.tgz && docker-php-ext-enable mongodb ; \
  pecl install /home/resource/xlswriter-1.3.7.tgz && docker-php-ext-enable xlswriter ; \
  pecl install /home/resource/zip-1.19.2.tgz && docker-php-ext-enable zip ;

RUN rm -rf /var/lib/apt/lists/* ; \
  apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false ; \
  rm -rf /home/resource ;
