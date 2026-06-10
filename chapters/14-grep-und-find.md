# Kapitel 14: grep und find

## Ziel

Du findest Inhalte in Dateien mit `grep` und Dateien im Verzeichnisbaum mit `find`. Beide Werkzeuge sind im Developer-Alltag täglich im Einsatz.

## Setup

```bash
mkdir -p kapitel-14-grep-find
cd kapitel-14-grep-find

mkdir -p src/api src/db
printf 'PORT=3000\nDATABASE_URL=postgres://localhost/dev\nSECRET=abc123\n' > .env
printf 'connect to $DATABASE_URL\nretry on error\n' > src/db/connect.sh
printf 'listen on $PORT\n# TODO: add auth\n' > src/api/server.sh
printf 'error: connection refused\ninfo: server started\nerror: timeout\n' > app.log
touch src/api/routes.sh src/db/migrate.sh
```

## Experiment 1: Muster in einer Datei suchen — grep

```bash
grep error app.log
grep -i error app.log
```

## Beobachten

Ohne `-i` ist `grep` case-sensitive. Mit `-i` findet es `error`, `Error`, `ERROR`.

## Experiment 2: Zeilennummern und invertierte Suche

```bash
grep -n error app.log
grep -v error app.log
```

## Beobachten

`-n` zeigt die Zeilennummer. `-v` invertiert: alle Zeilen ohne das Muster.

## Experiment 3: In mehreren Dateien suchen — grep -r

```bash
grep -r "TODO" src/
grep -r "DATABASE_URL" .
grep -rl "PORT" .
```

## Beobachten

`-r` durchsucht Verzeichnisse rekursiv. `-l` gibt nur Dateinamen aus, nicht den Inhalt — nützlich wenn man wissen will *wo* etwas vorkommt.

## Experiment 4: grep in einer Pipe

### Vorhersage

Was filtert diese Pipeline aus dem Log?

```bash
cat app.log | grep error | grep -v timeout
```

Docker-typisch:

```bash
# docker logs mycontainer | grep -i error
# Hier simulieren wir es mit unserer Log-Datei:
cat app.log | grep -i error
```

## Experiment 5: Dateien im Verzeichnisbaum finden — find

```bash
find . -name "*.sh"
find . -name ".env"
find src/ -type f
```

## Beobachten

`-name` sucht nach Dateiname (mit Glob). `-type f` findet nur Dateien (kein Verzeichnisse). `find` gibt immer Pfade aus.

## Experiment 6: find mit Tiefenbegrenzung

```bash
find . -maxdepth 1 -type f
find . -maxdepth 2 -name "*.sh"
```

## Experiment 7: find und grep kombinieren

Alle Shell-Skripte, die "TODO" enthalten:

```bash
grep -rl "TODO" $(find . -name "*.sh")
```

Oder mit `-exec`:

```bash
find . -name "*.sh" -exec grep -l "TODO" {} +
```

## Merksatz

`grep` durchsucht Inhalte, `find` durchsucht Pfade. In Kombination decken sie die meisten "Wo ist das?" Fragen im Developer-Alltag ab.

## Cleanup

```bash
cd ..
rm -rf kapitel-14-grep-find
```

## Nächstes Kapitel

Weiter mit [`15-entrypoint-script.md`](15-entrypoint-script.md).
