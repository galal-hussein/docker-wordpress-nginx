FROM ubuntu:14.04
ENV chached_FLAG 1

RUN apt-get -yqq update
RUN apt-get -yqq install wget
ADD run.sh /run.sh

VOLUME [ "/var/www/app" ]
WORKDIR /var/www/app

ENTRYPOINT ["/bin/bash","/run.sh"]

