FROM nginx:stable-alpine

LABEL vendor="0+X"
LABEL maintainer="Sebastian Mandrean <sebastian@0x.se>"

RUN rm -rf /usr/share/nginx/html && mkdir -p /usr/share/nginx/html

ADD default.conf /etc/nginx/conf.d/default.conf
