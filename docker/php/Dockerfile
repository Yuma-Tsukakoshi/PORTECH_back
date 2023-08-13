FROM php:8.1.17-fpm-alpine3.17
COPY php.ini /usr/local/etc/php/

# 必要なパッケージをインストール
RUN apk add --no-cache \
  libzip-dev \
  zlib-dev \
  mariadb-client \
  unzip \
  curl \
  vim \
  && docker-php-ext-install zip pdo_mysql sockets \
  && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer \
  && composer self-update --2 \
  && echo 'export PATH="$PATH:$HOME/.composer/vendor/bin"' >> ~/.bashrc

# PHPの設定ファイルをコピー
COPY php.ini /usr/local/etc/php/conf.d/custom.ini

# ワーキングディレクトリを設定
WORKDIR /work/web

