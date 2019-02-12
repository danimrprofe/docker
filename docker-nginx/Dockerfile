FROM nginx:latest

RUN apt-get update -q && \
    apt-get dist-upgrade -y

RUN rm /etc/nginx/conf.d/default.conf

RUN mkdir -p /srv/www/html && \
    chown nginx:nginx /srv/www/html

COPY nginx_main_site.conf /etc/nginx/conf.d

COPY test.txt /srv/www/html/
