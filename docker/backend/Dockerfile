FROM php:7.4-fpm


RUN apt-get update && apt-get install -y \
      apt-utils \
      libpq-dev \
      libpng-dev \
      libonig-dev \
      libxml2-dev \
      libzip-dev \
      zip unzip \
      nano \
      supervisor && \
      docker-php-ext-install pdo_pgsql && \
      docker-php-ext-install mbstring && \
      docker-php-ext-install exif && \
      docker-php-ext-install bcmath && \
      docker-php-ext-install pcntl && \
      docker-php-ext-install gd && \
      docker-php-ext-install zip && \
      apt-get clean && \
      rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

COPY ./docker/backend/php.ini /usr/local/etc/php/conf.d/php.ini

# Install composer
ENV COMPOSER_ALLOW_SUPERUSER=1
RUN curl -sS https://getcomposer.org/installer | php -- \
    --filename=composer \
    --install-dir=/usr/local/bin


EXPOSE 9000

#CMD ["php-fpm"]