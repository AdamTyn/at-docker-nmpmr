FROM php:7.2.10-fpm

COPY resource /home/resource

ARG CHANGE_SOURCE=false

ARG TIME_ZONE=UTC

ENV TIME_ZONE=${TIME_ZONE}

ENV LC_ALL=C.UTF-8

RUN ln -snf /usr/share/zoneinfo/$TIME_ZONE /etc/localtime ; \
  echo $TIME_ZONE > /etc/timezone ;
  
RUN mv /home/resource/phpunit-6.5.3.phar /usr/local/bin/phpunit ; \
  chmod 755 /usr/local/bin/phpunit ;

RUN mv /home/resource/composer.phar /usr/local/bin/composer ; \
  chmod 755 /usr/local/bin/composer ; \
  \
  rm -rf /etc/apt/sources.list.d/buster.list ; \
  if [ ${CHANGE_SOURCE} = true ]; then \
  mv /etc/apt/sources.list /etc/apt/source.list.bak; \ 
  mv /home/resource/tsinghua.list /etc/apt/sources.list; \
  composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/ ; \
  fi;

RUN apt-get clean \ 
  && apt-get update --fix-missing ;

RUN apt-get install -y --allow-remove-essential --no-install-recommends \
  libmagickwand-dev \
  procps \
  git \
  zip \
  unzip \
  libtool \
  libzip-dev  \
  libtinfo5 \
  libpq-dev \
  libfreetype6-dev \
  libjpeg62-turbo-dev \
  libpng-dev \
  libevent-dev \
  librdkafka-dev \
  libmcrypt-dev \
  libmhash-dev;

RUN docker-php-ext-configure gd \
  --with-freetype-dir=/usr/include/ \
  --with-jpeg-dir=/usr/include/ ; \
  docker-php-ext-install -j$(nproc) gd pdo_mysql mysqli soap pcntl bcmath; \
  pecl install /home/resource/imagick-3.4.4.tgz && docker-php-ext-enable imagick; \
  pecl install /home/resource/rdkafka-3.1.2.tgz && docker-php-ext-enable rdkafka; \
  pecl install /home/resource/event-2.5.3.tgz && docker-php-ext-enable event; \
  pecl install /home/resource/nsq-3.4.3.tgz && docker-php-ext-enable nsq; \
  pecl install /home/resource/redis-5.0.2.tgz && docker-php-ext-enable redis; \
  pecl install /home/resource/swoole-4.4.7.tgz && docker-php-ext-enable swoole; \
  pecl install /home/resource/mcrypt-1.0.3.tgz && docker-php-ext-enable mcrypt; \
  pecl install /home/resource/mongodb-1.6.0.tgz && docker-php-ext-enable mongodb; \
  pecl install /home/resource/zip-1.15.5.tgz && docker-php-ext-enable zip;

RUN rm -rf /var/lib/apt/lists/* ; \
  apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false ; \
  rm -rf /home/resource ;