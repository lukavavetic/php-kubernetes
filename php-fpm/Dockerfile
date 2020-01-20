FROM php:7.2-fpm

# Replace shell with bash so we can source files
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

# make sure apt is up to date
RUN apt-get update --fix-missing
RUN apt-get install -y curl git
RUN apt-get install -y build-essential libssl-dev zlib1g-dev libpng-dev libjpeg-dev libfreetype6-dev

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

#LIB_XML#
RUN apt install -y libxml2-dev \
#########################

#OPENSSL#
&& apt install -y openssl \
#########################

#PDO#
&& docker-php-ext-install pdo pdo_mysql \
#########################

#SOCKET#
&& docker-php-ext-install sockets \
####################################

#JSON#
&& docker-php-ext-install json \
###################################

#SOAP#
&& docker-php-ext-install soap \
##################################

#MBSTRING#
&& docker-php-ext-install mbstring \
#########################

#OPCACHE#
&& docker-php-ext-install opcache \
#########################

#MAIL PARSE#
&& pecl install -o -f mailparse \
&&  rm -rf /tmp/pear \
&& docker-php-ext-enable mailparse \
#########################

#NODE#
&& apt-get install -y curl \
&& curl -sL https://deb.nodesource.com/setup_9.x | bash - \
&& apt-get install -y nodejs \
&& curl -L https://www.npmjs.com/install.sh | sh \
#########################

#SASS#
&& npm install node-sass \
#########################

#IMAGEMAGICK#
&& apt-get install -y libmagickwand-dev imagemagick && \
pecl install imagick && \
docker-php-ext-enable imagick \
#########################

#EXIF#
&& docker-php-ext-install exif \
&& docker-php-ext-enable exif \
#########################

#GD#
&& docker-php-ext-configure gd --with-freetype-dir=/usr/lib/ --with-png-dir=/usr/lib/  --with-jpeg-dir=/usr/lib/ --with-gd \
&& docker-php-ext-install gd
#########################

ADD ./app /var/www/app

#RUN composer update

EXPOSE 9000
