# Mini Projekt | Manuel Santoro

Mein eigenes Dockerfile enthält folgendes:

```
# Datei MiniProjket_Msantoro 
FROM httpd:2.4
LABEL Manuel Santoro "manuel.santoro@edu.gbssg.ch" 
ARG DEBIAN_FRONTEND=noninteractive
COPY ./santoro /var/www/html
```
### Erklärung
|Code |Erklärung |
| ----------- | ----------- |
|**# Datei MiniProjket_Msantoro** | Dateiname |
|**FROM httpd:2.4** | Verwendung des httpd-Images V 2.4 als Basisimage |
|**LABEL Manuel Santoro "manuel.santoro@edu.gbssg.ch"** | Namen und E-Mail-Adresse des Entwicklers (ich) |
|**ARG DEBIAN_FRONTEND=noninteractive**  | ist dazu da um Error ausgaben während dem Build zu minimieren |
|**COPY ./santoro /var/www/html** | Kopiert Ordner mit den HTML Files vom Host-System in das Verzeichnis "/var/www/html" im Container (dort holt apache2 die Webseiten her) |

**Quelle:**<br>
[httpd (Dockedrhub)](https://www.example.com)





