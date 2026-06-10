# Kapitel 09: Werkzeuge – Dateien lesen und Text verarbeiten

## Ziel

Du lernst die wichtigsten Werkzeuge für den täglichen Umgang mit Textdateien und Ausgaben kennen: `man`, `cat`, `less`, `head`, `tail`, `wc`, `sort`, `tee`.

## Setup

```bash
mkdir -p kapitel-09-werkzeuge
cd kapitel-09-werkzeuge
printf 'alpha\nbeta\ngamma\nalpha\nbeta\n' > words.txt
seq 1 20 > lines.txt
```

## Experiment 1: Hilfe — man

```bash
man echo
```

Navigieren: Pfeiltasten, `q` verlässt die Seite, `/Suchbegriff` sucht.

```bash
man grep
```

## Beobachten

`man` zeigt die offizielle Handbuchseite. Sektion 1 = Benutzerprogramme. `man 1 ls` erzwingt Sektion 1.

## Experiment 2: Datei anzeigen — cat, less

```bash
cat words.txt
```

Bei langen Dateien:

```bash
less lines.txt
```

`less` blättert seitenweise. `q` verlässt, `/` sucht, `G` springt ans Ende, `g` an den Anfang.

## Experiment 3: Anfang und Ende — head, tail

### Vorhersage

Was zeigt `head -3 lines.txt`?

```bash
head -3 lines.txt
tail -3 lines.txt
```

Tail ohne Argument zeigt die letzten 10 Zeilen. Besonders nützlich für Logs:

```bash
tail -f lines.txt
```

`Ctrl+C` bricht ab. `-f` folgt einer Datei, die weiter wächst.

## Experiment 4: Zählen — wc

```bash
wc -l words.txt
wc -w words.txt
wc -c words.txt
```

## Beobachten

`-l` = Zeilen, `-w` = Wörter, `-c` = Bytes. Kombinierbar mit Pipes:

```bash
cat words.txt | wc -l
```

## Experiment 5: Sortieren und deduplizieren — sort

```bash
sort words.txt
sort -u words.txt
```

## Beobachten

`sort` verändert die Originaldatei nicht, es schreibt auf stdout. `-u` entfernt Duplikate.

## Experiment 6: Ausgabe in Pipe und in Datei gleichzeitig — tee

### Vorhersage

Wenn du die Ausgabe eines Befehls sowohl auf dem Terminal sehen als auch in eine Datei schreiben willst — was machst du?

```bash
echo "hallo" | tee tee-demo.txt
cat tee-demo.txt
```

Jetzt mit einer Pipe:

```bash
sort words.txt | tee sorted.txt | wc -l
cat sorted.txt
```

## Beobachten

`tee` ist ein T-Stück in der Pipe: stdout geht gleichzeitig an die Datei und weiter in die nächste Pipe.

## Merksatz

`cat`, `less`, `head`, `tail`, `wc`, `sort`, `tee` arbeiten auf stdin oder Dateien und schreiben auf stdout. Sie lassen sich beliebig mit Pipes kombinieren.

## Cleanup

```bash
cd ..
rm -rf kapitel-09-werkzeuge
```

## Nächstes Kapitel

Weiter mit [`10-dateiverwaltung.md`](10-dateiverwaltung.md).
