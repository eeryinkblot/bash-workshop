# Sprechtext: grep & find (Folien 13–15, ~15 min)

Kapitelmaterial: [`chapters/14-grep-und-find.md`](../../../chapters/14-grep-und-find.md)

## Folie: 14 — grep & find

Zwei Fragen, die ihr im Developer-Alltag täglich habt: „Wo *steht* das?" — also in welcher Datei kommt dieser String vor — und „Wo *liegt* das?" — also wo im Verzeichnisbaum ist diese Datei. Dafür gibt es zwei Werkzeuge, und das Setup in Kapitel 14 baut dafür ein kleines Mini-Projekt mit `.env`, Quellcode und einer Log-Datei. Erst das Setup ausführen, dann Experimente 1 und 2: `grep` auf das Log, mit `-i` für case-insensitive, `-n` für Zeilennummern, `-v` für invertierte Suche.

## Folie: Arbeitsteilung

Die Arbeitsteilung: `grep` durchsucht Inhalte, `find` durchsucht Pfade. Experiment 3 zeigt `grep -r` für rekursive Suche über ganze Verzeichnisse — und `-l`, wenn man nur wissen will, in *welchen Dateien* etwas steht. Dann Experimente 5 und 6 mit `find`: `-name` mit Glob-Muster — Achtung, das Muster gehört in Quotes, sonst expandiert Bash es vorher, das ist wieder unser mentales Modell! — `-type f` für nur-Dateien, `-maxdepth` gegen zu viel Output. Wer schnell ist, kombiniert in Experiment 7 beide mit `-exec`.

## Folie: Merksatz

Der Alltagsgriff Nummer eins: `docker logs app | grep -i error`. Container loggt auf stdout, die Pipe aus dem letzten Abschnitt schiebt das in grep, fertig ist die Fehlersuche. In Experiment 4 simulieren wir genau das mit unserer Log-Datei. Wer das einmal verinnerlicht hat, debuggt Container schneller als mit jedem Dashboard. Merksatz: grep für Inhalte, find für Pfade — zusammen decken sie fast jede „Wo ist das?"-Frage ab.
