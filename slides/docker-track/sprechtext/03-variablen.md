# Sprechtext: Variablen & Export (Folien 10–12, ~15 min)

Kapitelmaterial: [`chapters/03-variablen.md`](../../../chapters/03-variablen.md)

## Folie: 03 — Variablen

Frage in die Runde: Wann wird `$name` eigentlich ersetzt — beim Zuweisen, beim Ausführen, oder irgendwann dazwischen? Antwort aus unserem mentalen Modell: Bash ersetzt die Variable beim Verarbeiten der Zeile, bevor das Programm startet. Jetzt die Experimente 1 und 2 aus Kapitel 03 laufen lassen. Klassiker für Einsteiger: Bei der Zuweisung keine Leerzeichen um das `=` — `MYSENTENCE=A sentence` versucht, ein Programm namens `sentence` zu starten. Das ist kein Bug, das ist die Wort-Zerlegung aus Abschnitt 01 in Aktion.

## Folie: Zwei Welten

Single Quotes gegen Double Quotes — Experiment 3: In Double Quotes wird `$MYSTRING` expandiert, in Single Quotes bleibt es wörtlich der Text `$MYSTRING`. Dann Experiment 4, das Glob-Experiment: Eine unquoted Variable, die einen Stern enthält, löst beim Lesen *nochmal* Globbing aus. Das ist der Grund für den wichtigsten Reflex dieses Abschnitts. Danach Experiment 5, Export: Eine normale Variable existiert nur in der aktuellen Shell. Erst `export` legt sie in die Umgebung, die Kindprozesse erben. Das demonstriert der `bash -c`-Test eindrücklich.

## Folie: Merksatz

Merksatz: `"$var"` mit Double Quotes ist der sichere Default — unquoted nur, wenn man Word Splitting wirklich will, und das ist selten. Und die Docker-Brücke: Alles, was ihr über Umgebungsvariablen wisst, ist genau dieser Mechanismus. `docker run -e`, die `environment:`-Sektion in Compose, `.env`-Dateien — das ist nichts anderes als Export in die Prozessumgebung des Containers. Im Entrypoint-Script prüfen wir nachher genau solche Variablen.
