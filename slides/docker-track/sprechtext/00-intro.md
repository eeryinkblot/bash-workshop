# Sprechtext: Intro & Umgebung (Folien 1–4, ~5 min)

Kapitelmaterial: [`chapters/00-umgebung.md`](../../../chapters/00-umgebung.md)

## Folie: Titel

Willkommen! In den nächsten 90 Minuten geht es um genau das Bash, das ihr im Developer-Alltag mit Docker, CI und kleinen Skripten wirklich braucht. Kein Vollkurs, kein Theoriemarathon — am Ende habt ihr ein echtes, produktionsreifes Entrypoint-Script geschrieben. Mit euren eigenen Händen, in eurem eigenen Terminal.

## Folie: Heute

Der Fahrplan: Wir starten mit einem kurzen Check, ob bei allen Bash läuft, und bauen ein mentales Modell auf — was macht Bash eigentlich mit einer Zeile, bevor ein Programm startet? Dann die vier Bausteine, aus denen fast alles besteht: Pipes und Redirects, Variablen, grep und find, und die Verkettungs-Operatoren. Am Schluss setzen wir alles zu einem Entrypoint-Script zusammen, wie es in echten Containern läuft. Jeder Baustein zahlt direkt auf das Finale ein.

## Folie: 00 — Umgebung

Erste Frage, ganz praktisch: Läuft bei euch wirklich Bash? Auf dem Mac ist die Standard-Shell inzwischen zsh, in manchen Containern läuft nur sh. Öffnet bitte ein Terminal und führt die Befehle aus Kapitel 00 aus — `echo "$BASH_VERSION"` ist der schnellste Test. Kommt da nichts, tippt einfach `bash` und ihr seid drin. Wartet kurz, bis alle ein grünes Häkchen haben — vergleichbare Umgebungen ersparen uns später viel Verwirrung.

## Folie: Spielregeln

Drei Spielregeln für heute. Erstens: Vor jedem Codeblock kurz überlegen — was glaube ich, was gleich passiert? Zweitens: ausführen. Drittens: Ausgabe anschauen und mit der Vorhersage vergleichen. Genau in der Lücke zwischen Erwartung und Realität lernt man Bash. Und keine Sorge: Wir arbeiten ausschließlich in einem Wegwerf-Ordner. Wenn etwas schiefgeht, löschen wir den Ordner und fangen neu an. Legt ihn jetzt an — der Befehl steht in Kapitel 00.
