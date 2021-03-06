FROM php:5.6.40-fpm-stretch

LABEL maintainer="Vincent Letourneau <vincent@nanoninja.com>"

RUN apt-get update && apt-get upgrade -y \
    && apt-get install -y \
    gettext-base \
    g++ \
    libbz2-dev \
    libc-client-dev \
    libcurl4-gnutls-dev \
    libedit-dev \
    libfreetype6-dev \
    libicu-dev \
    libjpeg62-turbo-dev \
    libkrb5-dev \
    libldap2-dev \
    libmagickwand-dev \
    libmcrypt-dev \
    libmemcached-dev \
    libpq-dev \
    libsqlite3-dev \
    libssh2-1-dev \
    libssh2-1 \
    libssl-dev \
    libreadline-dev \
    libxslt1-dev \
    memcached \
    mc \
    net-tools \
    procps \
    procinfo \
    tcpdump \
    unzip \
    zlib1g-dev \
    locales \
    gettext-base \
    lsb-release \
    wget \
    && ln -snf /usr/share/zoneinfo/Europe/Moscow /etc/localtime && echo 'Europe/Moscow' > /etc/timezone \
    && docker-php-ext-configure gd \
    --with-freetype-dir=/usr/include/ \
    --with-jpeg-dir=/usr/include/ \
    --with-png-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-configure imap --with-kerberos --with-imap-ssl \
    && docker-php-ext-install -j$(nproc) imap \
    && docker-php-ext-configure intl \
    && docker-php-ext-install -j$(nproc) intl \
    && docker-php-ext-configure ldap --with-libdir=lib/x86_64-linux-gnu/ \
    && docker-php-ext-install ldap \
    && docker-php-ext-install -j$(nproc) \
    bcmath \
    bz2 \
    calendar \
    exif \
    gettext \
    mbstring \
    mcrypt \
    mysql \
    mysqli \
    opcache \
    pdo_mysql \
    pdo_pgsql \
    pgsql \
    soap \
    sockets \
    xmlrpc \
    xsl \
    zip \
    && pecl install xdebug-2.5.5 && docker-php-ext-enable xdebug \
    && pecl install memcached-2.2.0 && docker-php-ext-enable memcached \
    && pecl install mongodb && docker-php-ext-enable mongodb \
    && pecl install redis && docker-php-ext-enable redis \
    && pecl install ssh2 && docker-php-ext-enable ssh2 \
    && yes '' | pecl install imagick && docker-php-ext-enable imagick \
    && docker-php-source delete \
    && apt-get remove -y g++ wget \
    && apt-get autoremove --purge -y && apt-get autoclean -y && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /tmp/* /var/tmp/* \
    && echo 'ru_RU.UTF-8 UTF-8' >>  /etc/locale.gen && locale-gen \
    && curl -sL https://getcomposer.org/installer | php -- --install-dir /usr/bin --filename composer \
    && echo 'end'

ENV TZ=Europe/Moscow
ENV LANG ru_RU.utf8
ENV LANGUAGE ru_RU:ru  
ENV LC_ALL=ru_RU.UTF-8
