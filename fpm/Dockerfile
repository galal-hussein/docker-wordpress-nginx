#dockerfile for nginx/php5-fpm
FROM ubuntu:14.04
MAINTAINER hussein.galal.ahmed.11@gmail.com
ENV CACHED_FLAG 1
ENV DEBIAN_FRONTEND noninteractive

# Install nginx and php-fpm
RUN apt-get update -qq && apt-get -y upgrade
RUN apt-get install -yqq php5-fpm php5-mysql
# Adding the configuration files
ADD conf/www.conf /etc/php5/fpm/pool.d/www.conf
ADD conf/php-fpm.conf /etc/php5/fpm/php-fpm.conf
VOLUME /var/www/app
# Add the run script to run the services and configure db
ADD run.sh /run.sh


# Expose the port 9000 
EXPOSE 9000

# Run the run.sh script
ENTRYPOINT [ "/bin/bash", "/run.sh"]
