FROM debian:jessie

RUN apt-get update && apt-get install -y nginx vim curl

ADD nginx.conf /etc/nginx/
ADD wordpress.conf /etc/nginx/sites-available/

RUN ln -s /etc/nginx/sites-available/wordpress.conf /etc/nginx/sites-enabled/wordpress
RUN rm /etc/nginx/sites-enabled/default

RUN echo "upstream php-upstream { server php:9000; }" > /etc/nginx/conf.d/upstream.conf

#ENV WORDPRESS_VERSION 4.5.3
#ENV# WORDPRESS_SHA1 835b68748dae5a9d31c059313cd0150f03a49269
#
## upstream tarballs include ./wordpress/ so this gives us /var/wordpress, but we rename it as /var/www
#RUN curl -o wordpress.tar.gz -SL https://wordpress.org/wordpress-${WORDPRESS_VERSION}.tar.gz \
#	&& echo "$WORDPRESS_SHA1 *wordpress.tar.gz" | sha1sum -c - \
#	&& tar -xzf wordpress.tar.gz -C /var/ \
#	&& rm wordpress.tar.gz \
#	&& rm -rf /var/www \
#	&& mv /var/wordpress /var/www \
#	&& chown -R www-data:www-data /var/www

RUN usermod -u 1000 www-data

CMD ["nginx"]

EXPOSE 80
EXPOSE 443
