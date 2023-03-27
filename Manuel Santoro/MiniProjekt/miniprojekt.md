# Mini Projekt | Manuel Santoro

Mein Dockerfile enthält folgendes:

```
# Datei MiniProjket_Msantoro 
FROM httpd:2.4
LABEL Manuel Santoro "manuel.santoro@edu.gbssg.ch" 
ARG DEBIAN_FRONTEND=noninteractive
COPY ./santoro /var/www/html
```

