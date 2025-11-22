FROM php:8.2-apache

# PHP 확장(pdo_mysql) 설치
RUN docker-php-ext-install pdo_mysql

# Apache 유용 모듈
RUN a2enmod rewrite

# Apache가 8080 포트로 리스닝하도록 설정 변경
RUN sed -i 's/80/8080/g' /etc/apache2/ports.conf /etc/apache2/sites-available/000-default.conf

EXPOSE 8080

# 타임존 설정 (php.ini에서 확정)
#WORKDIR web/
COPY web/php.ini /usr/local/etc/php/conf.d/99-custom.ini

# 문서 루트는 기본 /var/www/html (변경 필요 없으면 그대로)
WORKDIR /var/www/html
COPY app/ .
