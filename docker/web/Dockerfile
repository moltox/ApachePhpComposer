FROM php:8.0-apache

RUN apt-get update -yqq && \
    apt-get upgrade -y && \
    apt-get install -y apt-utils zip unzip && \
    apt-get install -y nano && \
    apt-get install -y libzip.dev libpq-dev && \
    apt-get install -y npm && \
    a2enmod rewrite && \
    docker-php-ext-install mysqli && \
    docker-php-ext-install pdo_mysql

RUN rm -rf /var/lib/apt/lists/*

RUN php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin --filename=composer

#RUN sed -i 's/memory_limit = .*/memory_limit='1024M'/' /usr/local/etc/php/php.ini-development

#RUN sed -i 's/memory_limit = .*/memory_limit='256M'/' /usr/local/etc/php/php.ini-production

RUN ln -s /usr/local/bin/php /usr/bin/php

COPY php.ini /usr/local/etc/php/conf.d/php.ini
COPY index.html /var/www/html/index.html
COPY info.php /var/www/html/info.php
COPY default.conf /etc/apache2/sites-enabled/000-default.conf

WORKDIR /var/www/app

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]

EXPOSE 80
