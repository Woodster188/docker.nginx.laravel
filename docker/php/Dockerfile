FROM composer as composer
FROM php:7.4-fpm
RUN apt-get update -y && apt-get upgrade -y
RUN apt-get install -y \
	cron \
	make \
	curl \
	zip \
	unzip \
	libzip-dev \
	librabbitmq-dev \
	libfreetype6-dev \
	libjpeg62-turbo-dev \
	libpng-dev \
	libicu-dev \
	g++ \
	gcc \
	libpcre3-dev \
	--no-install-recommends \
	libmagickwand-dev \
	libtool \
	htop \
	mc \
	nano \
	libxslt-dev
RUN rm -rf /var/lib/apt/lists/*
RUN docker-php-ext-install \
	pdo \
	zip \
	bcmath \
	pdo_mysql \
	mysqli \
	intl \
	xsl \
	shmop \
	sockets \
	gettext \
	pcntl \
	sysvmsg \
	sysvsem \
	sysvshm \
	opcache \
	&& \
	docker-php-ext-configure \
	gd \
	&& \
	docker-php-ext-install \
	gd
RUN pecl install \
	swoole \
	amqp && \
	docker-php-ext-enable \
	amqp \
	swoole
COPY --from=composer /usr/bin/composer /usr/bin/composer
WORKDIR /var/www/app
