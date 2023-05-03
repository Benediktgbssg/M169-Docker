# Docker Compose-Anleitung für WordPress mit MariaDB und phpMyAdmin

In dieser Anleitung wird gezeigt, wie man Docker Compose verwendet, um eine WordPress-Website mit MariaDB-Datenbank und phpMyAdmin zu erstellen. Wir werden auch vertrauliche Informationen wie Passwörter als Docker-Secrets speichern.

## Schritt 1: Docker und Docker Compose installieren

Stellen Sie sicher, dass Docker und Docker Compose auf Ihrem System installiert sind. Wenn Sie sie noch nicht installiert haben, folgen Sie den offiziellen Anweisungen auf der [Docker-Website](https://www.docker.com/) und der [Docker Compose-Website](https://docs.docker.com/compose/install/).

## Schritt 2: Verzeichnis erstellen und Docker Compose-Datei erstellen

Erstellen Sie ein neues Verzeichnis für Ihr WordPress-Projekt und navigieren Sie in dieses Verzeichnis. Erstellen Sie dann eine neue Datei mit dem Namen `docker-compose.yml` und fügen Sie den folgenden Code hinzu:

```
version: '3.9'

services: 
  db:  
    image: mariadb:latest
    container_name: mariadb
    environment:
      - MYSQL_ROOT_PASSWORD_FILE=/run/secrets/db_root_password
      - MYSQL_PASSWORD_FILE=/run/secrets/db_password
      - MYSQL_DATABASE=dbname
      - MYSQL_USER=user1
    networks:
      - net1
    volumes:
      - myvolume:/var/lib/mysql
    secrets:
      - db_root_password
      - db_password

  phpma:
    image: phpmyadmin:latest
    container_name: phpma
    ports:
      - "8080:80"
    environment:
      - PMA_HOST=mariadb

  wpress:
    image: wordpress:latest
    container_name: wordpress-test
    restart: unless-stopped
    ports:
      - "8081:80"
    environment:
      - WORDPRESS_DB_HOST=mariadb
      - WORDPRESS_DB_USER=user1
      - WORDPRESS_DB_NAME=dbname
      - WORDPRESS_DB_PASSWORD_FILE=/run/secrets/wp_password
    networks:
      - net1
    volumes:
      - wp-html:/var/www/html/wp-content
    secrets:
      - wp_password

volumes:
  myvolume:
  wp-html:

networks:
  net1:
    driver: bridge

secrets:
  db_root_password:
    file: /path/to/db_root_password.txt
  db_password:
    file: /path/to/db_password.txt
  wp_password:
    file: /path/to/wp_password.txt
```

Stellen Sie sicher, dass Sie die Dateipfade für die Passwort-Textdateien unter `secrets` aktualisieren.

## Schritt 3: Docker Secrets erstellen

Erstellen Sie jetzt Docker Secrets für Ihre Passwörter. Navigieren Sie dazu zum Verzeichnis, in dem sich Ihre Passwort-Textdateien befinden, und führen Sie die folgenden Befehle aus:

```
$ docker secret create db_root_password db_root_password.txt
$ docker secret create db_password db_password.txt
$ docker secret create wp_password wp_password.txt
```

## Schritt 4: Docker Compose starten

Starten Sie nun Docker Compose im Hintergrund mit dem folgenden Befehl:

```
$ docker-compose up -d
```

Dieser Befehl lädt alle erforderlichen Docker-Images herunter und erstellt die Container für die MariaDB-Datenbank, phpMyAdmin und WordPress.

##
