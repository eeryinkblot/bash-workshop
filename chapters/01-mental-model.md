# Kapitel 01: Mentales Modell: Was macht Bash?

## Ziel

Du entwickelst ein erstes Modell dafür, was Bash mit einer eingegebenen Zeile macht, bevor ein Programm läuft.

## Leitfrage

Wenn du `ls *` eingibst: Wer sieht den Stern? Bash? `ls`? Das Betriebssystem?

## Befehlsarten untersuchen

```bash
type echo
type cd
type ls
type grep
type pwd
```

## Beobachten

Nicht jeder Befehl ist gleich:

- Manche Befehle sind Bash-Builtins.
- Manche Befehle sind Programme auf dem Dateisystem.
- Manche Namen können später auch Funktionen oder Aliases sein.

## Pfade von Programmen ansehen

```bash
command -v ls
command -v grep
command -v cd
```

## Mini-Experiment: Programm oder Shell?

```bash
printf '<%s>\n' hello world
```

Jetzt mit mehreren Leerzeichen:

```bash
printf '<%s>\n' hello        world
```

Jetzt mit Quotes:

```bash
printf '<%s>\n' "hello        world"
```

## Beobachten

- Ohne Quotes werden Wörter getrennt.
- Mit Quotes bleibt der Text als ein Argument zusammen.
- `printf` zeigt hier nur sichtbar, welche Argumente angekommen sind.

## Merksatz

Bash liest die Zeile, verarbeitet Expansionen und Wörter, und ruft danach Builtins, Funktionen oder Programme auf.

Viele Bash-Überraschungen passieren, bevor das aufgerufene Programm überhaupt startet.

## Cleanup für dieses Kapitel

Kein Cleanup nötig.

## Nächstes Kapitel

Weiter mit [`02-globbing-und-quoting.md`](02-globbing-und-quoting.md).
