FROM amazonlinux:2

# timezone environment
ENV TZ=Asia/Tokyo \
  # locale
  LANG=ja_JP.UTF-8 \
  LANGUAGE=ja_JP:ja \
  LC_ALL=ja_JP.UTF-8

RUN yum update -y \
  && yum install -y \
  glibc-langpack-ja \
  zip \
  unzip \
  vim \
  httpd

RUN amazon-linux-extras install -y epel
RUN yum install -y https://rpms.remirepo.net/enterprise/remi-release-7.rpm

RUN yum clean metadata \
  && yum install -y \
  php81 \
  php81-php \
  php81-php-mbstring \
  php81-php-pdo \
  php81-php-xml \
  php81-php-fpm \
  php81-php-mysqlnd \
  php81-php-gd

RUN alternatives --install /usr/bin/php php /usr/bin/php81 1

# composer のインストール
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer
ENV COMPOSER_ALLOW_SUPERUSER 1

# ファイルのコピー
COPY ./infra/docker/php/php.ini /etc/opt/remi/php81/php.ini
COPY ./infra/docker/apache/vhost.conf /etc/httpd/conf.d/vhost.conf
COPY ./infra/docker/apache/rewrite.conf /etc/httpd/conf.modules.d/rewrite.conf

CMD [ "apachectl", "-D", "FOREGROUND" ]

WORKDIR /work/backend
