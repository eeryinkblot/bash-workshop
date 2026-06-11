# Sprechtext: Mentales Modell (Folien 5–6, ~10 min)

Kapitelmaterial: [`chapters/01-mental-model.md`](../../../chapters/01-mental-model.md)

## Folie: 01 — Mentales Modell

Die wichtigste Frage des ganzen Workshops: Wenn ihr `ls *` eintippt — wer sieht den Stern? Lasst kurz raten: Bash? Das Programm `ls`? Das Betriebssystem? Die meisten tippen auf `ls`. Falsch — und dieses Missverständnis ist die Quelle der meisten Bash-Überraschungen.

Die Antwort: Bash expandiert den Stern zu einer Liste von Dateinamen, *bevor* `ls` überhaupt startet. `ls` bekommt den Stern nie zu sehen, sondern fertige Dateinamen als Argumente.

Lasst die Gruppe jetzt die Experimente aus Kapitel 01 durchspielen: erst `type` auf ein paar Befehle — da sieht man, dass `cd` ein Builtin ist und `ls` ein Programm auf der Platte. Dann das printf-Experiment mit den vielen Leerzeichen: ohne Quotes werden die Wörter getrennt, mit Quotes bleibt alles ein Argument. `printf` ist hier nur unser Röntgengerät — es zeigt sichtbar, welche Argumente wirklich angekommen sind.

## Folie: Merksatz

Der Satz, den ihr aus dieser Viertelstunde mitnehmen sollt: Erst Bash, dann Programm. Bash liest die Zeile, macht Expansionen, zerlegt sie in Wörter — und erst dann startet das Programm. Wenn euch im Docker-Alltag etwas Komisches passiert, ein ENTRYPOINT sich seltsam verhält, eine Variable im Container leer ist: Die Erklärung liegt fast immer in diesem Schritt, nicht im Programm selbst. Dieses Modell tragen wir durch alle folgenden Abschnitte.
