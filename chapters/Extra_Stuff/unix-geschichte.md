# Extra: UNIX – Geschichte und Philosophie

## Kurze Geschichte

| Jahr | Ereignis |
|---|---|
| 1969 | Ken Thompson und Dennis Ritchie entwickeln UNIX bei Bell Labs |
| 1973 | UNIX in C umgeschrieben — erste portable OS-Implementierung |
| 1983 | Richard Stallman startet GNU-Projekt (freie UNIX-Alternative) |
| 1987 | MINIX erscheint als Lehrprojekt (Inspiration für Linux) |
| 1991 | Linus Torvalds veröffentlicht den Linux-Kernel |
| 1992 | Linux + GNU-Tools → erstes vollständiges freies System |

Bash entstand 1989 als freie Reimplementierung der Bourne Shell (sh, 1979).

## Die UNIX-Philosophie (nach Doug McIlroy)

1. **Ein Programm soll eine Sache gut machen.**
2. **Programme sollen zusammenarbeiten.**
3. **Programme sollen mit Textströmen arbeiten — das ist die universelle Schnittstelle.**

Das ist der Grund, warum `cat | grep | sort | wc` funktioniert: jedes Tool ist simpel, aber zusammen sind sie mächtig.

## Schwächen von UNIX/Bash

- Fehler in Pipes werden standardmäßig verschluckt (→ `set -o pipefail`)
- Kein Echtzeitbetriebssystem
- Wenig aussagekräftige Verzeichnisnamen (`/usr`, `/var`, `/etc`)
- Keine Rückfragen bei gefährlichen Kommandos (`rm -rf /`)
- **"No news is good news"**: kein Output bedeutet Erfolg — kein Feedback für Anfänger

## POSIX-Standard

POSIX (Portable Operating System Interface) definiert eine gemeinsame Schnittstelle für UNIX-ähnliche Systeme. Skripte, die nur POSIX-sh nutzen, laufen auf Bash, Dash, Zsh und anderen. Bash-spezifische Features (`[[ ]]`, Prozesssubstitution, Arrays) sind nicht POSIX.

## Dateisystem-Hierarchie unter Linux

| Pfad | Inhalt |
|---|---|
| `/` | Root — Ausgangspunkt des gesamten Baums |
| `/bin`, `/usr/bin` | Systemprogramme und Benutzerprogramme |
| `/etc` | Konfigurationsdateien |
| `/home` | Benutzerverzeichnisse |
| `/var` | Variable Daten: Logs, Caches, Datenbanken |
| `/tmp` | Temporäre Dateien (beim Reboot gelöscht) |
| `/dev` | Gerätedateien — alles sind Dateien |
| `/proc` | Kernel- und Prozessinformationen als Dateipseudo-FS |
| `/mnt`, `/media` | Einhängepunkte für externe Speicher |
