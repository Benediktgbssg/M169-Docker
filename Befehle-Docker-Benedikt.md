# Benedikt

docker run [kleinschreibung des namen]
Beispiel: docker run hello-world

Wenn man visual studio cdes öffnet und Docker ist Installiert dann kann man die extension herunter laden. 

Mit {docker ps -a} kann man alle laufende Container einsehen.
-a steht hier für alle

Mit {docker images -a} kann man alle images auflisten.

Mit {docker image rm [name des container]} kann man ein image/ container löschen. Weil es bei mir noch am laufen war musste ich es mit -f forcen da es sonst nicht funktionierte.
{docker image rm hello-world -f}

docker rm [name des container nicht des images. Bei docker ps -a kann man den container name sehen.]
Nach diesem befehl ist bei docker ps -a hello world nicht mehr seh bar.

container interaktiv erstellen/ machen

docker run -it [name des image]

Fragen von Praxis aufgaben:
1. Wie setzt sich der Image-name zusammen. [hersteller/name]
2. Wie können sie das lokale Image wieder auffrischen? sudo docker pull [image name]
3. Warum funktionieren die Kommandos ip addr oder ping nicht? Weil die container so abgespeckt wird damit sie klein sind das der command nicht installiert ist.
4. Welche Namen hat ihr Container und wie können Sie diesen erneut ausführen? 

## Getting started

docker run -d -p 8080:80 docker/getting-started

erklärung command:  -d für detached modus (demon)
                    -p 8080:80 für port umleitung 8080 ist auf was es umgeleitet wird. Und 80 ist was es normalerweise wäre.

Mit portainer kann man eine grafische darstellung aufrufen.
In dem man im browser localhost:9443 "sucht"


# Lektion3
### Aufgabe Mariadb:

1.

command zum starten:
docker run -d --name pleasework -e MYSQL_ROOT_PASSWORD=work mariadb

-d für dämond damit er im hintergrund läuft.
--name für sptezifischen namen geben. (nicht zwingend)
-e wird gemacht um eine eingabe zu machen (weil es im dämon modus gestartet wurde kann man ja nicht manuel eingeben) 

[MYSQL_ROOT_PASSWORD=work] ist die variable namen und work ist bei mir das Password.

Das ist nicht Praxistaublich weil das Password im befehl ist.

2. 

[docker inspect <container-name>]
{docker inspect pleasework}

Mit diesem befel kann man sehr viele Information über den Container ausgeben.

### Aufgabe Mariadb Update:

{docker run -d --name pleasework -e MYSQL_ROOT_PASSWORD=work -v /home/vmadmin/varlibmysql/:/var/lib/mysql mariadb}

Mit [-v /home/vmadmin/varlibmysql/:/var/lib/mysql] kann man den Ordner /var/lib/mysql das im container von Mariadb mit dem Ordner home/vmadmin/varlibmysql/ das Lokal auf dem Gerät ist verbinden.

Die anderen atributen wurde weiter oben erklärt.




# Lektion 4

### Aufgabe 1.5 Komunikation zwischen container

#### network erstellen

Befehl:
docker network create [name]

### Aufgab 1.6

#### Mariadb container
docker run -d --name mariadbt --network net1 -e MYSQL_RANDOM_ROOT_PASSWORD=1 -e MYSQL_DATABASE=dbname -e MYSQL_USER=user1 -e MYSQL_PASSWORD=user1password -v myvolume:/var/lib/mysql mariadb

#### PHPmyAdmin
docker run -d --name phpma --network net1 -p 8080:80 -e PMA_HOST=mariadbt phpmyadmin/phpmyadmin

#### Wordpress
docker run -d --name wordpress-test --network net1 -h worpress-titel -v wp-html:/var/www/html/wp-content -p 8081:80 -e WORDPRESS_DB_HOST=mariadbt -e WORDPRESS_DB_USER=user1 -e WORDPRESS_DB_NAME=dbname -e WORDPRESS_DB_PASSWORD=user1password wordpress


### Prüfung
#### Remove

Images: docker rmi [Image name]

Volumes: docker volume rm [vlume name]
