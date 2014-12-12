#dockerfile for nginx/php5-fpm
FROM ubuntu:14.04
MAINTAINER hussein.galal.ahmed.11@gmail.com
ENV CACHED_FLAG 1

# Install nginx and php-fpm
RUN apt-get update -qq && apt-get -y upgrade
RUN apt-get -y -qq install nginx
VOLUME /var/www/app

# Adding the configuration files
ADD conf/nginx.conf /etc/nginx/nginx.conf
ADD conf/default    /etc/nginx/conf.d/default
# Expose the port 80 
EXPOSE 80

# Run nginx
ENTRYPOINT [ "/usr/sbin/nginx" ]
