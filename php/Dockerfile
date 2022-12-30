FROM php:8.1.10-fpm

RUN apt-get update
RUN apt-get install unzip
RUN apt-get install -y emacs
RUN apt-get install -y libpq-dev && \
    docker-php-ext-install pdo pdo_pgsql pgsql

# Composerのインストール
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php composer-setup.php --install-dir=/usr/local/bin --filename=composer
RUN php -r "unlink('composer-setup.php');"

RUN mkdir -p /var/run/php-fpm
VOLUME ["/var/run/php-fpm"]

COPY zz-docker.conf /usr/local/etc/php-fpm.d/zz-docker.conf

COPY php.ini /usr/local/etc/php/php.ini

RUN mkdir -p /var/www/html/example-app
COPY ./example-app /var/www/html/example-app

WORKDIR /var/www/html/example-app