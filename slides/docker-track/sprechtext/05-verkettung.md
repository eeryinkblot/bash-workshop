# Sprechtext: Verkettung & set -euo pipefail (Folien 16–18, ~10 min)

Kapitelmaterial: [`chapters/13-history-prompt-verkettung.md`](../../../chapters/13-history-prompt-verkettung.md)

Hinweis: Im Docker-Track nutzen wir aus Kapitel 13 nur die Experimente 4 und 5 — History und Prompt überspringen wir aus Zeitgründen, sie eignen sich als Homework-Hinweis.

## Folie: 13 — Verkettung

Vorhersagefrage: `ls gibt-es-nicht && echo "nach dem Fehler"` — wird das echo ausgeführt? Erst raten lassen, dann Experiment 4 aus Kapitel 13 laufen lassen. Die Auflösung: Nein, denn `&&` führt die rechte Seite nur aus, wenn die linke mit Exit Code 0, also Erfolg, beendet wurde. Jeder Befehl hinterlässt einen Exit Code — 0 heißt Erfolg, alles andere heißt Fehler. Das ist das stille Rückgrat der Fehlerbehandlung in Bash.

## Folie: Drei Operatoren

Die drei Operatoren im Vergleich: `&&` macht nur bei Erfolg weiter — der häufigste in Skripten und in Dockerfiles, denkt an die langen `RUN apt-get update && apt-get install`-Ketten. `||` ist das Gegenteil: nur bei Fehler weiter, perfekt für Fallbacks. Und `;` ist der Gleichgültige: macht immer weiter, egal was links passiert ist. Kurz ausprobieren lassen, die drei Varianten stehen im Kapitel direkt untereinander.

## Folie: Merksatz

Jetzt Experiment 5, der Sicherheitsgurt: Ohne Schutz läuft ein Skript nach einem Fehler einfach weiter — im Container heißt das: die App startet, obwohl die Migration fehlgeschlagen ist. `set -e` bricht beim ersten Fehler ab. Die volle Kombination `set -euo pipefail` gehört in die zweite Zeile jedes Skripts: `-e` bricht bei Fehlern ab, `-u` meckert bei unbelegten Variablen, `-o pipefail` sorgt dafür, dass Fehler mitten in einer Pipe nicht verschluckt werden. Diese Zeile schreiben wir gleich ganz oben in unser Entrypoint-Script.
