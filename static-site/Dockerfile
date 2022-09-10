FROM php:apache-buster

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y vim

COPY index.html /var/www/html/