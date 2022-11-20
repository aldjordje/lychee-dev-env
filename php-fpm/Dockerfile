FROM php:8.1-fpm

RUN apt-get update; \
    apt-get -y --no-install-recommends install \
        git \
        ffmpeg \
        gifsicle \
		jpegoptim \
		libimage-exiftool-perl \
		optipng \
		pngquant \
		libzip-dev \
		unzip \
		webp \
		libmagickwand-dev

RUN docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/		

RUN docker-php-ext-install \
		bcmath \
		exif \
		mysqli \
		pdo_mysql \
		gd \
		zip 

RUN pecl install \
		xdebug \
		imagick

RUN docker-php-ext-enable \
		xdebug \
		imagick

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin/ --filename=composer

RUN usermod -u 1000 www-data && \
    groupmod -g 1000 www-data
