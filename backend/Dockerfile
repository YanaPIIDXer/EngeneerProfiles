FROM php:8.0-apache

RUN apt-get update && \
    apt-get install -y git unzip libzip-dev libicu-dev libonig-dev && \
    docker-php-ext-install intl pdo_mysql zip bcmath
RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin

ADD ./php.ini /usr/local/etc/php/
RUN sed -i 's!/var/www/html!/var/www/html/app/public!g' /etc/apache2/sites-available/000-default.conf

WORKDIR /var/www/html/app

ADD ./src /var/www/html/app

# 参考:https://qiita.com/ryotaro0999/items/3b47ee0ceb310278ac3a
RUN chown -R www-data:www-data /var/www && \
    chmod -R 777 /var/www/html/app/storage

EXPOSE 80
