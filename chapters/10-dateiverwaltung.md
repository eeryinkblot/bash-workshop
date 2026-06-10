# Kapitel 10: Dateiverwaltung – cp, mv, rm, mkdir

## Ziel

Du kannst Dateien und Verzeichnisse kopieren, verschieben, umbenennen und löschen. Du kennst die wichtigsten Gefahren dabei.

## Setup

```bash
mkdir -p kapitel-10-dateiverwaltung
cd kapitel-10-dateiverwaltung
touch datei1.txt datei2.txt datei3.txt
mkdir -p unterordner/tief
```

## Experiment 1: Kopieren — cp

```bash
cp datei1.txt datei1-kopie.txt
ls
```

Einen Ordner mit allem darin kopieren:

```bash
cp -r unterordner unterordner-kopie
ls
```

## Beobachten

Ohne `-r` schlägt `cp` bei Verzeichnissen fehl. `-r` steht für rekursiv.

## Experiment 2: Verschieben und umbenennen — mv

```bash
mv datei2.txt datei2-umbenannt.txt
ls
```

```bash
mv datei3.txt unterordner/
ls unterordner/
```

## Beobachten

`mv` hat keine `-r` Flag – es bewegt Verzeichnisse immer als Ganzes.

## Experiment 3: Löschen — rm

### Vorhersage

Was passiert, wenn du `rm unterordner` ohne Flags aufrufst?

```bash
rm datei2-umbenannt.txt
rm unterordner
```

```bash
rm -r unterordner
ls
```

## Beobachten

`rm` löscht ohne Rückfrage und ohne Papierkorb. `-r` löscht Verzeichnisse rekursiv. Es gibt kein Zurück.

## Experiment 4: Verzeichnisse anlegen und entfernen — mkdir, rmdir

```bash
mkdir -p neu/a/b/c
ls -R neu
rmdir neu/a/b/c
rmdir neu/a/b
rmdir neu/a
rmdir neu
```

## Beobachten

`rmdir` entfernt nur leere Verzeichnisse. `-p` bei `mkdir` legt alle fehlenden Ebenen auf einmal an.

## Experiment 5: Navigation — cd, pwd, ~

```bash
pwd
cd kapitel-10-dateiverwaltung 2>/dev/null || true
echo ~
cd ~
pwd
cd -
pwd
```

## Beobachten

`cd` ohne Argument und `cd ~` gehen ins Home-Verzeichnis. `cd -` wechselt ins zuletzt besuchte Verzeichnis.

## Experiment 6: Langer Befehl — Backslash-Zeilenfortsetzung

Backslash am Zeilenende sagt Bash: der Befehl geht in der nächsten Zeile weiter.

```bash
echo "eins" \
     "zwei" \
     "drei"
```

```bash
cp \
  datei1.txt \
  datei1-kopie.txt
```

## Beobachten

Das ist rein optisch – Bash liest den Backslash als Escapezeichen für den Zeilenumbruch. Der Befehl ist eine einzige Zeile.

## Merksatz

`rm` löscht sofort und unwiderruflich. Bei `rm -r` immer zweimal hinschauen, was der Pfad ist.

## Cleanup

```bash
cd ..
rm -rf kapitel-10-dateiverwaltung
```

## Nächstes Kapitel

Weiter mit [`11-rechte.md`](11-rechte.md).
