# docker build -t symfony-php-fpm:8.1.19 .
FROM php:8.1.19-fpm

WORKDIR /var/www/app

LABEL name="symfony-php-fpm" \
	desctiption="base php-fpm Docker Image" \
	version="0.1"

RUN apt-get update
RUN apt-get install -y git curl zip unzip vim nano htop wget mc

## COMPOSER
COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

## INSTALL Symfony CLI
RUN curl -sS https://get.symfony.com/cli/installer | bash
RUN mv /root/.symfony5/bin/symfony /usr/local/bin/symfony

## GIT
RUN git config --global user.email "dawidgos25@gmail.com" \
    && git config --global user.name "dgos"

## COPY FILES
RUN rm /root/.bashrc
ADD .bashrc /root/.bashrc
ADD .bash_aliases /root/.bash_aliases

