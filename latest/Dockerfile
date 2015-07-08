FROM richarvey/nginx-php-fpm
MAINTAINER Arthur Burkart <artburkart@gmail.com>

ENV DEBIAN_FRONTEND noninteractive
ENV INITRD No
ENV LANG C.UTF-8

# Install Phalcon dependencies
RUN apt-get update \
  && apt-get install -y --no-install-recommends php5-dev re2c make libpcre3-dev software-properties-common

# Uprade to latest PHP 5.5
RUN add-apt-repository ppa:ondrej/php5 -y \
  && apt-get update -y \
  && apt-get upgrade -y \
  && apt-get install php5 -y -o Dpkg::Options::="--force-confold" -o Dpkg::Options::="--force-confold"

# Install Phalcon
RUN git clone git://github.com/phalcon/cphalcon.git \
  && cd cphalcon/ext \
  && ./install \
  && mkdir -p /etc/php5/mods-available \
  && echo "extension=phalcon.so" > /etc/php5/mods-available/phalcon.ini

# Configure Phalcon and PHP
RUN echo "extension=phalcon.so" > /etc/php5/fpm/conf.d/21-phalcon.ini \
  && echo "extension=phalcon.so" > /etc/php5/cli/conf.d/21-phalcon.ini \
  && echo "extension=mcrypt.so" > /etc/php5/fpm/conf.d/22-mcrypt.ini \
  && echo "extension=mcrypt.so" > /etc/php5/cli/conf.d/22-mcrypt.ini \
  && sed -i -e "s/;opcache.enable=0/opcache.enable=1/g" /etc/php5/fpm/php.ini
