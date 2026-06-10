# Homework 07: Command Substitution, Exit Codes und Tests

1. Nutze `$(...)`, um das aktuelle Datum in eine Variable zu schreiben.
2. Prüfe Exit Codes von `ls`, `grep` und einem nicht existierenden Befehl.
3. Schreibe ein `if`, das abhängig von `grep` eine Meldung ausgibt.
4. Schreibe Tests für Datei existiert, Datei existiert nicht, Variable ist leer.

Startpunkt:

```bash
today=$(date +%F)
echo "$today"
```
