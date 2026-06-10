# Kapitel 12: Prozesse – ps, kill, Jobkontrolle

## Ziel

Du verstehst, was ein Prozess ist, wie du laufende Prozesse findest, wie du sie beendest und wie du Jobs im Hintergrund steuerst.

## Setup

```bash
mkdir -p kapitel-12-prozesse
cd kapitel-12-prozesse
```

## Experiment 1: Laufende Prozesse anzeigen — ps

```bash
ps
```

Alle Prozesse des Systems:

```bash
ps aux | head -20
```

Einen bestimmten Prozess suchen:

```bash
ps aux | grep bash
```

## Beobachten

Wichtige Spalten in `ps aux`:
- `PID` — Prozess-ID, eindeutige Nummer
- `%CPU` — CPU-Nutzung
- `%MEM` — Speichernutzung
- `COMMAND` — Befehl, der den Prozess gestartet hat

## Experiment 2: Shell verlassen — exit, Ctrl+D

```bash
echo "exit beendet die Shell"
# exit  ← auskommentiert, weil wir weitermachen wollen
```

`Ctrl+D` sendet EOF (End of File) an stdin. Die Shell interpretiert das als „keine Eingabe mehr" und beendet sich.

In einer Sub-Shell ausprobieren:

```bash
bash
echo "ich bin in einer neuen Shell, PID: $$"
exit
echo "zurück in der alten Shell"
```

## Beobachten

`$$` ist die PID der aktuellen Shell. `exit` und `Ctrl+D` beenden nur die aktuelle Shell-Instanz.

## Experiment 3: Prozess im Hintergrund starten

```bash
sleep 30 &
echo "PID des Sleep: $!"
jobs
```

## Beobachten

`&` startet den Prozess im Hintergrund. `$!` ist die PID des zuletzt in den Hintergrund geschickten Prozesses. `jobs` zeigt alle Hintergrundjobs der aktuellen Shell.

## Experiment 4: Prozess in den Vordergrund und Hintergrund — fg, bg, Ctrl+Z

Starte einen Prozess:

```bash
sleep 60
```

Drücke `Ctrl+Z`. Der Prozess wird gestoppt (nicht beendet).

```bash
jobs
bg
jobs
```

```bash
fg
```

Dann `Ctrl+C` um den Prozess abzubrechen.

## Beobachten

- `Ctrl+Z` — Prozess stoppen (pausieren), Job wechselt zu `[Stopped]`
- `bg` — gestoppten Job im Hintergrund weiterlaufen lassen
- `fg` — Job in den Vordergrund holen
- `Ctrl+C` — Prozess abbrechen (SIGINT senden)

## Experiment 5: Prozess beenden — kill

```bash
sleep 120 &
SLEEPPID=$!
echo "Sleep läuft mit PID: $SLEEPPID"
jobs
```

```bash
kill "$SLEEPPID"
jobs
```

Mit explizitem Signal:

```bash
sleep 120 &
kill -9 $!
```

## Beobachten

`kill` sendet standardmäßig SIGTERM — eine höfliche Aufforderung zum Beenden. Der Prozess kann darauf reagieren.

`kill -9` sendet SIGKILL — das Betriebssystem beendet den Prozess sofort, ohne Chance aufzuräumen. Letztes Mittel.

## Merksatz

Jeder Befehl in Bash ist ein Prozess mit einer PID. Prozesse können Eltern-Kind-Beziehungen haben. `Ctrl+C` bricht ab, `Ctrl+Z` pausiert, `fg`/`bg` steuern die Jobkontrolle.

## Cleanup

```bash
cd ..
rm -rf kapitel-12-prozesse
```

## Nächstes Kapitel

Weiter mit [`13-history-prompt-verkettung.md`](13-history-prompt-verkettung.md).
