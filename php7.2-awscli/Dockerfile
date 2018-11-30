FROM php:7.2-cli

LABEL maintainer="mordonez.sanchez@gmail.com"

RUN apt-get update \
    && apt-get install git wget python python-pip -y

RUN curl -fsSL https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer \
    && composer global require phpunit/phpunit ^7.0 --no-progress --no-scripts --no-interaction

RUN pip install --upgrade pip awsebcli awscli

ENV PATH /root/.composer/vendor/bin:$PATH

# Use the default production configuration
RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"
