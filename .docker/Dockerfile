FROM php:8.2-apache

ENV DEBIAN_FRONTEND=noninteractive
ENV TZ=Etc/UTC

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime \
    && echo $TZ > /etc/timezone

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        build-essential \
        ca-certificates \
        cron \
        git \
        mariadb-client \
        software-properties-common \
        unzip \
        wget \
    && a2enmod rewrite

RUN curl -sL https://deb.nodesource.com/setup_18.x | bash - \
    && apt-get install -y --no-install-recommends nodejs

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

COPY 000-default.conf /etc/apache2/sites-available/
