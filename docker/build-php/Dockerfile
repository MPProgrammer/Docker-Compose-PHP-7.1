
ARG phpbuild
FROM php:$phpbuild

RUN apt-get update \
	&& apt-get install -y libmcrypt-dev \
		libjpeg62-turbo-dev \
		libpcre3-dev \
		libpng-dev \
		libfreetype6-dev \
		libxml2-dev \
		libicu-dev \
		ffmpeg \
	&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
	&& docker-php-ext-install iconv intl mcrypt opcache pdo pdo_mysql mbstring soap gd

# INSTALL ZIP TO USE COMPOSER
RUN apt-get install -y \
    zlib1g-dev \
    libzip-dev \
    unzip
RUN docker-php-ext-install zip

# Imagick extension
RUN apt-get install -y libmagickwand-dev; \
    pecl install imagick; \
    docker-php-ext-enable imagick;

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer