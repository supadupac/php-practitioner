#FROM php:7.4-apache
FROM php:8.0.2-apache-buster
COPY ./app /var/www/html/
COPY .docker/vhost.conf /etc/apache2/sites-available/000-default.conf
RUN apt-get update && apt-get install -y  \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd
#install pecl and xdebug
RUN pecl install redis-5.3.2 \
    && pecl install xdebug-3.0.2 \
    && docker-php-ext-enable redis xdebug
#install pdo
RUN docker-php-ext-install pdo_mysql
#install mysql
RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli
#change permissions for apache folders
RUN chown -R www-data:www-data /var/www/html/ && a2enmod rewrite
#insert servername
RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf
#restart apache
RUN service apache2 restart

# docker build --file .docker/Dockerfile -t docker-tutorial .
# docker run -rm -p 8080:80 docker-tutorial
