FROM alpine:latest
LABEL maintainer="csthink tech@csthink.com"
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories \
    && apk update