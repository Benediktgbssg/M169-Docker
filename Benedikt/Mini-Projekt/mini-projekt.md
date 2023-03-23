# Mini-Projekt

Zuerst erstellt man die Dockerfile. Dafür habe ich einfach in VisualStudio code die Neue Datei erstellt und Dockerfile benennt.

Im Dockerfile habe ich das hier reingeschrieben: 
```
# Datei Dockerfile
FROM httpd:2.4
COPY home/Desktop/public-html /usr/local/apache2/htdocs/
```

<details><summary>Erklärung</summary>
Das habe ich als Kommentar hinzugefügt.
```
# Datei Dockerfile
```

| Syntax | Erklärung |
| ------------- | ------------- |
| FROM httpd:2.4  | From macht das dieses Image als Basis Image verwendet wird. Hier wird httpd verwendet mit der version 2.4  |
| COPY ./public-html /usr/local/apache2/htdocs/  | Der Copy command kopiert dateien vom Lokalem System in den Container. Hier wird  der Ordner public-html der sich im verzeichnis befindet in dem der Command ausgeführt wird in dem im Container befindeteten Ordner /usr/local/apache2/htdocs/ kopiert. |
</details>

## Building

```
docker build -t my-webserver .
```

## Reduzierte Abschnitte

<details><summary>Erklärung</summary>

docker build ist der base command.
-t steht für 
my-webserver ist der Image-name des Images das gebauen wird.
. erklärt das die dateien im verzeichniss sind in dem der Command ausgeführt wird.
</details>

## Image Runnen

```
docker run -d --name web -p 8080:80 my-webserver
```
<details><summary>Erklärung</summary>

| Command  | Erklärung |
| ------------- | ------------- |
| -d  | der Container läuft im hintergrund  |
| --name web  | Der Namen des Container ist web  |
| -p 8080:80  | -p steht für Port umleitung. Hier wird der Port von 80 zu 8080 geändert  |
| my-webserver  | mein Image heisst my-webserver  |

</details>