FROM php:5.6-apache
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
        libxml2-dev \
    && docker-php-ext-install -j$(nproc) iconv mcrypt \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
	&& a2enmod rewrite \
	&& pecl install xdebug \
    && docker-php-ext-enable xdebug \
	&& echo "yes" | pecl install memcache \
	&& docker-php-ext-enable memcache \
	&& docker-php-ext-install pdo pdo_mysql soap
#	&& apt-get install -y \
#		php5-mysql \
#		php5-xdebug \
#		php5-memcache \
#	&& php5enmod xdebug \
#	&& php5enmod memcache \
