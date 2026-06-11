# Sprechtext: Entrypoint-Script & Abschluss (Folien 19–22, ~15 min)

Kapitelmaterial: [`chapters/15-entrypoint-script.md`](../../../chapters/15-entrypoint-script.md)

## Folie: 15 — Entrypoint-Script

Jetzt das Finale. Ein Entrypoint ist das erste Skript, das beim Containerstart läuft: Es prüft die Konfiguration, wartet auf Abhängigkeiten und startet dann die eigentliche Anwendung. Genau das bauen wir jetzt — und jeder Baustein der letzten 75 Minuten kommt darin vor. Experiment 1 aus Kapitel 15: die Pflichtprüfung mit `${VAR:?Meldung}`. Lasst das Skript einmal *ohne* Variablen laufen — saubere, lesbare Fehlermeldung statt kryptischem Absturz — und einmal mit. Das ist Variablen-Wissen aus Abschnitt 03 plus die stderr-Disziplin aus Abschnitt 05.

## Folie: Das Skript kann

Experiment 2: auf eine Abhängigkeit warten. Der Klassiker — der App-Container startet schneller als die Datenbank. Die `until`-Schleife probiert die TCP-Verbindung über `/dev/tcp/host/port`, ein Bash-eigener Trick, so lange, bis sie klappt oder der Timeout zuschlägt. Fehlermeldungen gehen mit `>&2` auf stderr, der Timeout führt zu `exit 1` — der Exit Code, auf den `&&` und Docker-Healthchecks reagieren. Dann Experiment 3: das vollständige Script. Lasst es alle mit dem `echo`-Testbefehl laufen — bei laufendem Beispiel ist der Stolz im Raum spürbar.

## Folie: Warum exec "$@"?

Die letzte Zeile ist die wichtigste: `exec "$@"`. `exec` ersetzt den Shell-Prozess vollständig durch den übergebenen Befehl — die App *wird* der Prozess, im Container PID 1. Warum ist das wichtig? Bei `docker stop` schickt Docker SIGTERM an PID 1. Ohne `exec` wäre die Shell PID 1, würde das Signal abfangen, und die App würde nach 10 Sekunden hart gekillt statt sauber heruntergefahren. Diese eine Zeile unterscheidet ein Spielzeug-Script von einem produktionsreifen Entrypoint. Und `"$@"` in Quotes — das ist unser Quoting-Reflex aus Abschnitt 03.

## Folie: Geschafft!

Zeit für die Abschlussrunde. Schaut auf die Tabelle am Ende von Kapitel 15: Jede Zeile dieses Scripts nutzt etwas, das ihr heute gelernt habt — `set -euo pipefail`, Variablenprüfung, stderr, Exit Codes, `exec`. Ihr habt nicht über ein Entrypoint-Script geredet, ihr habt eins geschrieben. Wer weitermachen will: Die Kapitel unter `chapters/` enthalten alle Experimente zum Nachspielen, `HOMEWORK.md` hat Vertiefungsaufgaben, und `chapters/Extra_Stuff/container-cicd.md` führt das Docker-Thema weiter. Danke fürs Mitmachen!
