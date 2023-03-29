# Mini-Projekt

Zuerst erstellt man die Dockerfile. Dafür habe ich einfach in VisualStudio code die Neue Datei erstellt und Dockerfile benennt.

Im Dockerfile habe ich das hier reingeschrieben: 
```
# Datei Dockerfile
FROM httpd:2.4
COPY home/Desktop/public-html /usr/local/apache2/htdocs/
COPY ./my-httpd.conf /usr/local/apache2/conf/httpd.conf
```

<details><summary>Erklärung</summary>
Das habe ich als Kommentar hinzugefügt.
```
# Datei Dockerfile
Das Basis Image ist httpd:2.4
Copy home/Desktop/public-html /usr/local/apache2/htdocs/ macht das die HTMl die ich in public-html zu /usr/local/apache2/htdocs/ kopiert. Sie müssen in htdocs sein damit die Webseite gehostet wird.
COPY ./my-httpd.conf /usr/local/apache2/conf/httpd.conf Ich habe das conf File heraus kopiert um zu änderen was alles gelogt wird. Jetzt kopiere ich es mit diesem Command wieder rein damit die ändereung verwendet werden.
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

<details><summary>Erklärung</summary>

docker build ist der base command.
-t steht für 
my-webserver ist der Image-name des Images das gebauen wird.
. erklärt das die dateien im verzeichniss sind in dem der Command ausgeführt wird.
</details>

## Image Runnen

```
docker run -d --name web -p 8080:80 -v /home/vmadmin/Desktop/dock/html_log/:/usr/local/apache2/logs/ -v /home/vmadmin/Desktop/dock/html_html/:/usr/local/apache2/htdocs/ my-webserver 
```
<details><summary>Erklärung</summary>

| Command  | Erklärung |
| ------------- | ------------- |
| -d  | der Container läuft im hintergrund  |
| --name web  | Der Namen des Container ist web  |
| -p 8080:80  | -p steht für Port umleitung. Hier wird der Port von 80 zu 8080 geändert  |
| -v /home/vmadmin/Desktop/dock/html_log/:/usr/local/apache2/logs/ | Es wird ein Volume erstellt die den Docker Host (VM) Ordner html_log mit den logs von httpd verbindent |
| -v /home/vmadmin/Desktop/dock/html_html/:/usr/local/apache2/htdocs/ | Es wird ein Volume erstellt die denn Docker Host (VM) Ordner html_html in dem die Webseiten gespeichert sind mit htdocs auf dem Container verbindet. Die Webseiten in htdocs werden von httpd gehosted. |
| my-webserver  | mein Image heisst my-webserver  |

</details>