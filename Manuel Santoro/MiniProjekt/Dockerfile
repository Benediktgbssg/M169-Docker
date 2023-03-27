# Datei MiniProjket_Msantoro 

# Version 1.0 (don't works fully)

FROM ubuntu:20.04 
LABEL Manuel Santoro "manuel.santoro@edu.gbssg.ch" 
ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get update && \
    apt-get install -y apache2 && \
    chown -R $USER:$USER /var/www/html/ && \
    chmod -R 777 /var/www/html/ && \
    a2ensite 000-default.conf && \
    #chmod 777 ./web-data && \
    apt-get clean && \ 
    rm -rf /var/lib/apt/lists/* 
COPY ./santoro /var/www/html
EXPOSE 8080


CMD ["/bin/bash"]

# Version 1.1

FROM httpd:2.4
LABEL Manuel Santoro "manuel.santoro@edu.gbssg.ch" 
ARG DEBIAN_FRONTEND=noninteractive
COPY ./santoro /var/www/html

docker build -t ownsite .
docker run -dit --name mywebsite -p 8080:80 ownsite
