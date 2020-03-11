
FROM nginx:1.16.0-alpine AS release

COPY ./default.nginx.conf /etc/nginx/conf.d/default.conf

ADD ./ /usr/share/nginx/html