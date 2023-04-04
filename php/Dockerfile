FROM php:8.1-fpm

# Install required dependencies
RUN apt-get update && \
    apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        libonig-dev \
        libzip-dev \
        locales \
        git \
        vim \
        curl \
        unzip \
        libxrender1 \
        libfontconfig1 \
        libx11-dev \
        libjpeg-dev \
        libxtst6 \
        libffi-dev \
        libcairo2 \
        libpango-1.0-0 \
        libpangocairo-1.0-0 \
        libgdk-pixbuf2.0-0 \
        libgtk-3-0 \
        libnss3 \
        libgconf-2-4 \
        libatk1.0-0

# Install Node.js
RUN curl -sL https://deb.nodesource.com/setup_16.x | bash -
RUN apt-get install -y nodejs
RUN npm install npm@latest -g

# Install PHP extensions
RUN docker-php-ext-install pdo_mysql mysqli gd iconv exif zip bcmath

# Install Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Copy php.ini
COPY ./php.ini /usr/local/etc/php/
