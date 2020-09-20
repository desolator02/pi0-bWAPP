Code copied from https://github.com/raesene/bWAPP.git

#Steps to install mySql

apt update
apt install mysql-server


method 1
RUN groupadd -r mysql && useradd -r -g mysql mysql

RUN set -xe \
    && apk add --no-cache --purge -uU \
        mysql \
        mysql-client \
        mariadb \
        mariadb-client \
        mariadb-backup \
        mariadb-server-utils \
        mariadb-mytop \
    && rm -rf /var/cache/apk/* /tmp/*
    
COPY root/ /

method 2
RUN apt-get update \
  && apt-get install -y mysql-server mysql-client libmysqlclient-dev --no-install-recommends \
  && docker-php-ext-install pdo pdo_mysql \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
