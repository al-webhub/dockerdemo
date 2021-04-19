FROM php:7.4-fpm

WORKDIR /var/www

RUN apt-get update && apt-get install -y  libonig-dev libpq-dev \
    build-essential \
    git \
    curl \
    zip \
    unzip \
    locales \
    libzip-dev \
    libpng-dev \
    libjpeg62-turbo-dev \
    libwebp-dev libjpeg62-turbo-dev libpng-dev libxpm-dev \
    libfreetype6 \
    libfreetype6-dev 

RUN apt-get clean && rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-install pdo_mysql mbstring zip exif pcntl
RUN docker-php-ext-configure gd --with-freetype --with-jpeg

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin/ --filename=composer

COPY . /var/www

EXPOSE 9000
CMD ["php-fpm"]

