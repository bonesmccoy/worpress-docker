FROM debian:jessie

RUN apt-get update && apt-get install -y vim curl

ENV WORDPRESS_VERSION 4.5.3
ENV WORDPRESS_SHA1 835b68748dae5a9d31c059313cd0150f03a49269

# upstream tarballs include ./wordpress/ so this gives us /var/wordpress, but we rename it as /var/www
RUN curl -o wordpress.tar.gz -SL https://wordpress.org/wordpress-${WORDPRESS_VERSION}.tar.gz \
	&& echo "$WORDPRESS_SHA1 *wordpress.tar.gz" | sha1sum -c - \
	&& tar -xzf wordpress.tar.gz -C /var/ \
	&& rm wordpress.tar.gz \
	&& rm -rf /var/www \
	&& mv /var/wordpress /var/www \
	&& chown -R www-data:www-data /var/www


COPY wp-config.php /var/www/wp-config.php

RUN usermod -u 1000 www-data
