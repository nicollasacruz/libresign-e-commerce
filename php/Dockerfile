FROM php:8.1-fpm

RUN apt-get update && apt-get install libzip-dev ca-certificates curl gnupg -y \
    # Add any necessary PHP extensions here
    && docker-php-ext-install pdo_mysql zip

RUN mkdir -p /etc/apt/keyrings

RUN curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg
RUN echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_20.x nodistro main" | tee /etc/apt/sources.list.d/nodesource.list

RUN apt-get update && apt-get install nodejs -y
RUN npm install npm -g

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www/html

RUN usermod -u 1000 www-data

CMD ["php-fpm"]