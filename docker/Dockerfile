FROM php:8.2-fpm


RUN apt-get update && apt-get install -y \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip \
    git \
    curl && \
    docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd


WORKDIR /var/www/html


COPY --from=composer /usr/bin/composer /usr/bin/composer


COPY yii2-app/ /var/www/html/


RUN composer install --no-dev --optimize-autoloader


CMD ["php-fpm"]

