# Sprechtext: Pipes & Redirects (Folien 7–9, ~15 min)

Kapitelmaterial: [`chapters/05-pipes-und-redirects.md`](../../../chapters/05-pipes-und-redirects.md)

## Folie: 05 — Pipes & Redirects

Einstiegsfrage: Ihr pipet die Ausgabe eines Befehls durch `grep` — und trotzdem erscheint eine Fehlermeldung ungefiltert auf dem Bildschirm. Warum geht die Fehlermeldung nicht durch die Pipe? Vorhersagen sammeln, dann die Experimente 1 bis 4 aus Kapitel 05 laufen lassen: erst Redirect in eine Datei, dann `>` gegen `>>` — überschreiben gegen anhängen — dann die Pipe, und schließlich der Aha-Moment: `cat` auf eine Datei, die nicht existiert, gepiped durch `grep`. Die Fehlermeldung landet trotzdem im Terminal.

## Folie: Drei Kanäle

Die Auflösung: Jeder Prozess hat drei Standardkanäle. stdin ist der Eingang, stdout der normale Ausgang, und stderr ist ein *zweiter*, separater Ausgang nur für Fehler. Die Pipe verbindet ausschließlich stdout mit stdin — stderr fließt daran vorbei, direkt ins Terminal. Das ist Absicht: So sieht man Fehler auch dann, wenn die normale Ausgabe weiterverarbeitet wird. Jetzt die Experimente 5 bis 7: stderr mit `2>` in eine Datei umleiten, dann beide Kanäle mit `2>&1` zusammenführen. Beim Reihenfolge-Experiment ruhig Zeit lassen — `2>&1` heißt: stderr zeigt ab jetzt dorthin, wohin stdout *in diesem Moment* zeigt. Redirects werden von links nach rechts ausgewertet.

## Folie: Merksatz

Merksatz: Die Pipe verbindet stdout mit stdin, stderr läuft daran vorbei. Und der Docker-Bezug ist direkt: `docker logs` zeigt euch stdout und stderr des Containers — Anwendungen in Containern loggen genau auf diese beiden Kanäle, nicht in Dateien. Wer die Kanäle versteht, versteht Container-Logging. Und im Entrypoint-Script am Ende schreiben wir Fehlermeldungen ganz bewusst mit `>&2` auf stderr.
