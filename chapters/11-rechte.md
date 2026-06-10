# Kapitel 11: Rechte und Eigentümer – chmod, chown, ls -l

## Ziel

Du verstehst das Unix-Rechtesystem mit Eigentümer, Gruppe und anderen. Du kannst Rechte mit `chmod` setzen und `ls -l` lesen.

## Setup

```bash
mkdir -p kapitel-11-rechte
cd kapitel-11-rechte
touch testdatei.txt
```

## Experiment 1: Rechte anzeigen — ls -l

```bash
ls -l testdatei.txt
ls -la
```

## Beobachten

Die erste Spalte zeigt die Rechte als 10 Zeichen:

```
-rw-r--r--
```

| Position | Bedeutung |
|---|---|
| 1 | Typ: `-` = Datei, `d` = Verzeichnis, `l` = Symlink |
| 2–4 | Rechte des Eigentümers (user) |
| 5–7 | Rechte der Gruppe (group) |
| 8–10 | Rechte aller anderen (others) |

Jede Dreiergruppe: `r` = lesen, `w` = schreiben, `x` = ausführen.

## Experiment 2: Rechte ändern — chmod symbolisch

```bash
chmod u+x testdatei.txt
ls -l testdatei.txt
```

```bash
chmod g-r testdatei.txt
ls -l testdatei.txt
```

```bash
chmod o+w testdatei.txt
ls -l testdatei.txt
```

## Beobachten

`u` = user, `g` = group, `o` = others, `a` = all. `+` fügt hinzu, `-` entfernt, `=` setzt exakt.

## Experiment 3: Rechte ändern — chmod oktal

### Vorhersage

Was bedeutet `chmod 755`?

```bash
chmod 755 testdatei.txt
ls -l testdatei.txt
```

```bash
chmod 644 testdatei.txt
ls -l testdatei.txt
```

```bash
chmod 777 testdatei.txt
ls -l testdatei.txt
```

## Beobachten

Jede Stelle ist eine Ziffer von 0–7:
- `r` = 4, `w` = 2, `x` = 1
- 7 = 4+2+1 = rwx, 5 = 4+0+1 = r-x, 4 = r--

`chmod 777` gibt allen vollen Zugriff. Bei Produktionssystemen fast immer zu viel.

## Experiment 4: Eingeloggte Benutzer — who, whoami

```bash
whoami
who
```

## Beobachten

`whoami` zeigt den aktuellen Benutzer. `who` zeigt alle angemeldeten Benutzer auf dem System.

## Experiment 5: Eigentümer wechseln — chown

```bash
ls -l testdatei.txt
```

`chown` braucht sudo. Syntax zur Kenntnis:

```bash
# chown benutzername:gruppenname datei.txt
```

Gruppe einer Datei anzeigen:

```bash
stat testdatei.txt
```

## Merksatz

`ls -l` lesen können ist wichtiger als alle Zahlen auswendig zu kennen. `chmod 644` für Dateien und `chmod 755` für ausführbare Dateien sind die häufigsten Werte.

## Cleanup

```bash
cd ..
rm -rf kapitel-11-rechte
```

## Nächstes Kapitel

Weiter mit [`12-prozesse.md`](12-prozesse.md).
