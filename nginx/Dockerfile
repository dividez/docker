FROM nginx:alpine

MAINTAINER luoyan <975974740@qq.com>

ADD nginx.conf /etc/nginx/

ARG PHP_UPSTREAM=php-fpm

#RUN echo 'http://mirrors.ustc.edu.cn/alpine/v3.4/main/' | cat - /etc/apk/repositories > /etc/apk/temp && mv /etc/apk/temp /etc/apk/repositories
#RUN echo 'http://mirrors.ustc.edu.cn/alpine/v3.4/main/' > /etc/apk/repositories
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/' /etc/apk/repositories

RUN apk update \
    && apk upgrade \
    && apk add --no-cache bash \
    && adduser -D -H -u 1000 -s /bin/bash www-data \
    && rm /etc/nginx/conf.d/default.conf \
    && echo "upstream php-upstream { server ${PHP_UPSTREAM}:9000; }" > /etc/nginx/conf.d/upstream.conf

CMD ["nginx"]

EXPOSE 80 443