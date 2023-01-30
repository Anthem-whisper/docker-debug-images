FROM php:8.2-apache
# COPY --from=composer /usr/bin/composer /usr/bin/composer
RUN    php -r "readfile('https://getcomposer.org/installer');" | php \
    && mv /var/www/html/composer.phar /usr/bin/composer
RUN    sed -i "s@http://deb.debian.org@http://mirrors.aliyun.com@g" /etc/apt/sources.list \
    && apt clean \
    && apt-get update \
    && apt-get -y install libzip-dev libicu-dev \
    && docker-php-ext-install mysqli zip intl \
    && pecl install xdebug-3.2.0 \
    && docker-php-ext-enable xdebug \
    && echo "xdebug.mode=debug" >> /usr/local/etc/php/php.ini

# dbgpProxy, for multiuser debugging
# ssh, for tunnel
# RUN   curl https://xdebug.org/files/binaries/dbgpProxy -o /usr/bin/dbgpProxy \
#     && chmod +x /usr/bin/dbgpProxy \
#     && apt-get install ssh
