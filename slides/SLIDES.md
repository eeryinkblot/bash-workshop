# Folien-Outline

Die Folien sind Taktgeber. Code steht in den Kapitel-Markdowns, nicht auf den Folien.

## 00 Umgebung

- Ziel: Alle arbeiten in Bash.
- Frage: Welche Shell läuft wirklich?
- Verweis: `chapters/00-umgebung.md`

## 01 Mentales Modell

- Ziel: Bash verarbeitet die Zeile vor dem Programm.
- Frage: Wer interpretiert Wörter, Leerzeichen und Quotes?
- Merksatz: Erst Bash, dann Programm.

## 02 Globbing und Quoting

- Ziel: `*` ist kein Regex-Stern.
- Frage: Wer sieht den Stern?
- Merksatz: Globs werden von Bash zu Dateinamen expandiert.

## 03 Variablen

- Ziel: Werte setzen, lesen, quoten, exportieren.
- Frage: Wann wird `$name` ersetzt?
- Merksatz: `"$var"` ist der sichere Default.

## 04 Funktionen und Befehlsarten

- Ziel: Funktionen, Builtins, Programme, Aliases unterscheiden.
- Frage: Was ruft Bash bei diesem Namen auf?
- Merksatz: `type` fragen.

## 05 Pipes und Redirects

- Ziel: stdout, stderr und stdin trennen.
- Frage: Warum geht die Fehlermeldung nicht durch die Pipe?
- Merksatz: Pipe verbindet stdout mit stdin.

## 06 Skripte, PATH und source

- Ziel: Skripte ausführbar machen und Startkontext verstehen.
- Frage: Warum braucht man `./`?
- Merksatz: `source` läuft in der aktuellen Shell.

## 07 Command Substitution, Exit Codes und Tests

- Ziel: Ausgaben einsetzen und Exit Codes für Steuerfluss nutzen.
- Frage: Ist Exit Code 1 immer ein Fehler?
- Merksatz: Programme definieren ihre Exit-Code-Bedeutung.

## 08 Loops und Abschluss-Script

- Ziel: Konzepte in einem kleinen Script zusammenführen.
- Frage: Wo brauchen wir Quotes?
- Merksatz: Kleine Bash-Skripte werden robust durch bewusstes Quoting, Tests und Exit Codes.
