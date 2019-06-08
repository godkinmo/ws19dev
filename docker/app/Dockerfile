FROM ubuntu:18.04

MAINTAINER Jack Fong

RUN apt-get update \
    && apt-get install -y locales \
    && locale-gen en_US.UTF-8

ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update \
    && apt-get install -y apache2 ssh openssh-server curl vim zip unzip git software-properties-common sqlite3 \
    && add-apt-repository -y ppa:ondrej/php \
    && apt-get update \
    && apt-get install -y php7.3 php7.3-zip libapache2-mod-php7.3 php7.3-cli php7.3-gd \
       php7.3-mbstring php7.3-xml php7.3-mysql php-memcached php7.3-pgsql \
       php7.3-imap php7.3-curl php7.3-sqlite3 php-xdebug \
    && php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer
#    && apt-get remove -y --purge software-properties-common \
#    && apt-get -y autoremove \
#    && apt-get clean \
#    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN composer global require "laravel/installer"

RUN ln -sf /dev/stdout /var/log/apache2/access.log \
    && ln -sf /dev/stderr /var/log/apache2/error.log

COPY 000-default.conf /etc/apache2/sites-available/000-default.conf

RUN a2enmod rewrite

EXPOSE 3000

CMD apachectl -D FOREGROUND
