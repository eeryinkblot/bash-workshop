# Extra: Container und CI/CD

## Container — ein Prozess ohne Oberfläche

Ein Container ist ein Prozess mit eigenem Dateisystem, Netzwerk und Prozessraum. Er startet aus einem Image und läuft wie eine Appliance: kein Login-Prompt, kein Desktop.

```bash
# Container starten und direkt einen Befehl ausführen
docker run ubuntu:24.04 bash -c "echo Hallo aus dem Container"

# Interaktive Shell in Container
docker run -it ubuntu:24.04 bash

# Laufende Container anzeigen
docker ps

# Alle Container (auch gestoppte)
docker ps -a

# Container stoppen
docker stop <container-id>
```

## Was passiert bei einem Container ohne Shell?

```bash
# Container starten und per exec eine Shell öffnen
docker exec -it <container-id> bash
# Falls bash nicht vorhanden:
docker exec -it <container-id> sh
```

## Volumes — Daten aus dem Container

```bash
# Verzeichnis von Host in Container mounten
docker run -v /host/pfad:/container/pfad ubuntu:24.04 ls /container/pfad

# Named Volume
docker volume create meinvolume
docker run -v meinvolume:/data ubuntu:24.04 touch /data/test.txt
```

## Bash in CI/CD (GitHub Actions Beispiel)

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Build
        run: |
          set -euo pipefail
          echo "Baue Projekt..."
          ./build.sh
```

## Warum Bash der Standard in CI ist

- Jeder Linux-Container hat Bash
- Kein zusätzlicher Interpreter nötig
- Direkte Interaktion mit Dateisystem, Prozessen, Netzwerktools
- `set -euo pipefail` macht CI-Skripte robust: erster Fehler stoppt alles

## Beobachten

In CI-Systemen (GitHub Actions, GitLab CI, Jenkins) ist jeder `run:`-Block ein Bash-Skript. Alles aus diesem Workshop gilt dort 1:1.
