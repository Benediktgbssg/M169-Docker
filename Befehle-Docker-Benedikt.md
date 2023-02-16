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

# Getting started

docker run -d -p 8080:80 docker/getting-started

erklärung command:  -d für detached modus (demon)
                    -p 8080:80 für port umleitung 8080 ist auf was es umgeleitet wird. Und 80 ist was es normalerweise wäre.

Mit portainer kann man eine grafische darstellung aufrufen.
In dem man im browser localhost:9443 "sucht"
