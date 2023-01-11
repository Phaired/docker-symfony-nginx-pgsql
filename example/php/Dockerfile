FROM php:8.2.1-fpm-alpine3.17


RUN apk add --no-cache tzdata
ENV TZ=Europe/Paris

ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN chmod +x /usr/local/bin/install-php-extensions && install-php-extensions

RUN curl -o /usr/local/bin/composer https://getcomposer.org/download/latest-stable/composer.phar && \
    chmod +x /usr/local/bin/composer

RUN apk add --no-cache git bash &&  \
    curl -1sLf 'https://dl.cloudsmith.io/public/symfony/stable/setup.alpine.sh' | bash && apk add symfony-cli

WORKDIR /var/www/html

CMD ["php-fpm"]

EXPOSE 9000