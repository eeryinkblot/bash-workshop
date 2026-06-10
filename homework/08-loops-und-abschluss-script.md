# Homework 08: Loops und Abschluss-Script

1. Schreibe eine `for`-Schleife über mehrere Wörter.
2. Schreibe eine `for`-Schleife über Dateien.
3. Lies eine Datei Zeile für Zeile mit `while IFS= read -r line`.
4. Erweitere das Abschluss-Script so, dass es bei genau null Treffern einen eigenen Exit Code liefert.

Startpunkt:

```bash
mkdir -p hw-08-loops
cd hw-08-loops
printf 'one\ntwo\nthree\n' > numbers.txt
```

Cleanup:

```bash
cd ..
rm -rf hw-08-loops
```
