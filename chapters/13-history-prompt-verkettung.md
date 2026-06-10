# Kapitel 13: History, Prompt und Befehlsverkettung

## Ziel

Du nutzt die Shell-History effizienter, passt deinen Prompt an und kennst die Unterschiede zwischen `&&`, `||` und `;` bei der Befehlsverkettung.

## Setup

```bash
mkdir -p kapitel-13-history
cd kapitel-13-history
```

## Experiment 1: History anzeigen und nutzen

```bash
history | tail -20
```

Letzten Befehl wiederholen:

```bash
!!
```

Befehl aus History nach Nummer:

```bash
!100
```

Letzten Befehl mit bestimmtem Anfang wiederholen:

```bash
!echo
```

Rückwärtssuche in History: `Ctrl+R`, dann Suchbegriff tippen. Enter führt den gefundenen Befehl aus.

## Beobachten

History wird in `~/.bash_history` gespeichert und beim Beenden der Shell geschrieben.

## Experiment 2: Sensibles aus der History entfernen

Wenn du aus Versehen ein Passwort in der Kommandozeile eingegeben hast:

```bash
history -d $(history | tail -1 | awk '{print $1}')
```

Oder den aktuellen Shell-Verlauf komplett leeren (schreibt nicht in die Datei):

```bash
history -c
```

## Beobachten

`history -d N` löscht Eintrag mit Nummer N. Die Datei `~/.bash_history` wird erst beim Shell-Exit überschrieben — solange ist die Session-History maßgeblich.

## Experiment 3: Prompt anpassen — PS1

```bash
echo "$PS1"
```

Prompt temporär ändern:

```bash
PS1='[\u@\h \W]\$ '
```

```bash
PS1='\w $ '
```

## Beobachten

`PS1` ist die Variable für den primären Prompt. Sondersequenzen: `\u` = Benutzer, `\h` = Hostname, `\w` = aktueller Pfad, `\W` = nur letzter Ordner. Änderungen gelten nur für die aktuelle Session.

## Experiment 4: Befehlsverkettung — &&, ||, ;

### Vorhersage

Was passiert, wenn der erste Befehl fehlschlägt?

```bash
echo "eins" && echo "zwei"
ls gibt-es-nicht && echo "nach dem Fehler"
```

```bash
ls gibt-es-nicht || echo "Fallback: Fehler erkannt"
```

```bash
echo "eins" ; echo "zwei" ; echo "drei"
ls gibt-es-nicht ; echo "läuft trotzdem"
```

## Beobachten

| Operator | Bedeutung |
|---|---|
| `&&` | Führe rechts aus, nur wenn links Erfolg (Exit Code 0) |
| `\|\|` | Führe rechts aus, nur wenn links Fehler (Exit Code ≠ 0) |
| `;` | Führe rechts immer aus, unabhängig vom Exit Code |

`&&` ist der häufigste in Skripten: "Nur weitermachen, wenn der letzte Schritt geklappt hat."

## Experiment 5: set -euo pipefail

Ohne Schutz:

```bash
bash -c 'ls gibt-es-nicht; echo "läuft weiter trotz Fehler"'
```

Mit `set -e`:

```bash
bash -c 'set -e; ls gibt-es-nicht; echo "wird nicht erreicht"'
```

## Beobachten

`set -e` beendet das Skript beim ersten nicht-null Exit Code. Zusammen die übliche Kombination für robuste Skripte:

```bash
#!/usr/bin/env bash
set -euo pipefail
```

- `-e` — bei Fehler sofort abbrechen
- `-u` — Fehler bei unbelegten Variablen
- `-o pipefail` — Fehler in Pipes nicht verschlucken

## Merksatz

`&&` und `||` sind Kurzschluss-Operatoren: Sie entscheiden anhand des Exit Codes, ob der nächste Befehl läuft. Das ist kein Zufall, sondern das Herzstück davon, wie Bash Fehler behandelt.

## Cleanup

```bash
cd ..
rm -rf kapitel-13-history
```
