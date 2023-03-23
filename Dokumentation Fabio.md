# Dokumentation Docker
Von Fabio Bilger

Browser: localhost/9443

### Container interaktiv verwenden

|Befehle            |               |                                                                     |
| -------------------| ------------- |---------------------------------------------------------------------|
|docker run <name>  | Ladet einen Container herunter/führt ihn aus  | -d (Im Hintergrund), --name (eigenen Namen geben)|
|docker ps -a       | Zeigt einem Informationen über den Container an wie zum Beispiel den richtigen Namen|
|docker rm          | Löscht einen Container wieder | 
|docker inspect <name> | Zeigt einem viele Infos über einen Container an |
 


#### Docker run
 
Mit "docker run -e MYSQL_ROOT_PASSWORD=eigenes Passwort" kann man den container starten und eine Passworteingabe aufrufen. Das Passwort wird ebenfalls gleich gesetzt.

 
