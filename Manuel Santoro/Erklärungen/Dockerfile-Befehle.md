# Dockerfile-Befehle

Ein Dockerfile ist eine Textdatei, die die Anweisungen enthält, die Docker verwenden soll, um ein Docker-Image zu erstellen. Hier sind einige wichtige Befehle, die im Dockerfile verwendet werden können:

## FROM

Der FROM-Befehl gibt das Basisimage an, auf dem das neue Image aufbaut. Der Befehl wird normalerweise am Anfang des Dockerfiles verwendet und gibt das Betriebssystem an, auf dem das neue Image basieren soll, sowie den Basis-Container, auf dem das Image aufbauen soll.

Beispiel:
```
FROM ubuntu:latest
```

## RUN

Der RUN-Befehl führt Anweisungen innerhalb des Containers aus. Der Befehl kann verwendet werden, um Systemupdates durchzuführen, Bibliotheken oder Anwendungen zu installieren oder andere Anweisungen auszuführen, die notwendig sind, um das Image zu erstellen.

Beispiel:
```
RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip
```

## COPY

Der COPY-Befehl kopiert Dateien oder Verzeichnisse vom Host-System in das Docker-Image. Der Befehl kann verwendet werden, um Anwendungscode, Konfigurationsdateien oder andere Dateien in das Image zu kopieren.

Beispiel:
```
COPY app.py /app/
```

## WORKDIR

Der WORKDIR-Befehl setzt das Arbeitsverzeichnis innerhalb des Containers, in dem alle weiteren Anweisungen ausgeführt werden sollen.

Beispiel:
```
WORKDIR /app
```

## EXPOSE

Der EXPOSE-Befehl gibt an, auf welchen Port der Container hören soll. Der Befehl hat keine Auswirkungen auf das Host-System oder das Netzwerk, aber er informiert den Benutzer darüber, welcher Port auf dem Container verfügbar ist.

Beispiel:
```
EXPOSE 5000
```

## CMD

Der CMD-Befehl gibt die Standardanweisung an, die ausgeführt wird, wenn der Container gestartet wird. Der Befehl kann verwendet werden, um den primären Prozess oder die Anwendung zu starten, die im Container ausgeführt werden soll.

Beispiel:
```
CMD ["python3", "app.py"]
```

Dies sind einige der wichtigsten Befehle im Dockerfile. Es gibt jedoch viele andere Befehle und Optionen, die im Dockerfile verwendet werden können, um Docker-Images auf verschiedene Arten zu erstellen und zu konfigurieren.
