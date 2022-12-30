FROM nginx:1.20.1

COPY default.conf /etc/nginx/conf.d/default.conf

RUN mkdir -p /var/www/html/example-app
COPY ./example-app /var/www/html/example-app
