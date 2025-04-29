FROM php:8.2-fpm

# Install required PHP extensions
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip \
    git \
    curl && \
    docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd

# Set working directory
WORKDIR /var/www/html

# Install Composer
COPY --from=composer /usr/bin/composer /usr/bin/composer

# Copy Yii2 app source code only
COPY yii2-app/ /var/www/html/

# Install PHP dependencies
RUN composer install --no-dev --optimize-autoloader

# Start PHP-FPM
CMD ["php-fpm"]

