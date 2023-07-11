FROM php:8.1.3-apache
WORKDIR /var/www/html/

RUN apt-get clean
RUN apt-get update && apt-get install -y \
        zlib1g-dev libicu-dev g++ \
        libjpeg62-turbo-dev \
        libzip-dev \
        libpng-dev \
        libwebp-dev \
        libfreetype6-dev \
        libmariadb-dev \
    	libxml2-dev \
    	git \
    	zip \
    	unzip \
      wget \
      curl \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-configure gd --with-webp=/usr/include/webp --with-jpeg=/usr/include --with-freetype=/usr/include/freetype2/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install -j$(nproc) zip


RUN docker-php-ext-install mysqli



# COPY ./src/opencart/ /var/www/html/

COPY ./src/opencart-4.0.2.1-tr.zip /opt/

RUN unzip /opt/opencart-4.0.2.1-tr.zip -d /var/www/html/

RUN chmod -R 777 /var/www/

