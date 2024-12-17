# Dockerfile para Laravel
FROM php:8.3-fpm

# Instalar dependências
RUN apt-get update && apt-get install -y \
    default-mysql-client \
    git \
    unzip \
    curl \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    libzip-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install pdo_mysql mbstring gd xml zip    

# Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Configuração do Laravel
WORKDIR /var/www/html
COPY . .

# Instalar dependências do Laravel
RUN composer install

# Permissões
RUN chown -R www-data:www-data /var/www/html/storage /var/www/html/bootstrap/cache

# Porta para o Artisan
EXPOSE 8000

CMD ["php", "artisan", "serve", "--host=0.0.0.0", "--port=8000"]
