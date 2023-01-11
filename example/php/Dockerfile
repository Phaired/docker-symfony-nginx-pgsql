ARG PHP_IMAGE
FROM ${PHP_IMAGE}

RUN /bin/sh -c ln -snf /usr/share/zoneinfo/"Europe/Paris" /etc/localtime &&  \
    echo "Europe/Paris" > /etc/timezone &&  \
    printf '[PHP]\ndate.timezone = "%s"\n', "Europe/Paris" > /usr/local/etc/php/conf.d/tzone.ini &&  \
    "date"

ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN /bin/sh -c chmod +x /usr/local/bin/install-php-extensions && install-php-extensions

RUN /bin/sh -c curl -o /usr/local/bin/composer https://getcomposer.org/download/latest-stable/composer.phar && \
    chmod +x /usr/local/bin/composer

RUN /bin/sh -c apk add --no-cache git bash &&  \
    curl -1sLf 'https://dl.cloudsmith.io/public/symfony/stable/setup.alpine.sh' | bash && apk add symfony-cli

WORKDIR /var/www/html

CMD ["/bin/sh", "-c", "composer i -o ; php-fpm"]

EXPOSE 9000