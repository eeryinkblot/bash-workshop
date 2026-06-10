# Kapitel 05: Pipes und Redirects

## Ziel

Du verstehst stdout, stderr, stdin, Pipes und Redirects.

## Setup

```bash
mkdir -p kapitel-05-pipes
cd kapitel-05-pipes
printf 'alpha\nbeta\ngamma\nalpha beta\n' > words.txt
```

## Experiment 1: Redirect stdout in Datei

```bash
echo "Hallo Datei" > out.txt
cat out.txt
```

## Experiment 2: Überschreiben vs Anhängen

```bash
echo "erste Zeile" > append-demo.txt
echo "zweite Zeile" > append-demo.txt
echo "dritte Zeile" >> append-demo.txt
cat append-demo.txt
```

## Beobachten

`>` überschreibt, `>>` hängt an.

## Experiment 3: Pipe

```bash
cat words.txt | grep alpha
cat words.txt | grep -c alpha
```

## Beobachten

Die Pipe verbindet stdout des linken Befehls mit stdin des rechten Befehls.

## Experiment 4: stderr ist nicht stdout

```bash
cat words.txt
cat does-not-exist.txt
```

Jetzt mit Pipe:

```bash
cat does-not-exist.txt | grep anything
```

## Beobachten

Die Fehlermeldung geht nicht durch die normale Pipe, weil sie auf stderr geschrieben wird.

## Experiment 5: stderr umleiten

```bash
cat does-not-exist.txt 2> error.txt
cat error.txt
```

## Experiment 6: stdout und stderr zusammenführen

```bash
cat words.txt does-not-exist.txt > combined.txt 2>&1
cat combined.txt
```

## Experiment 7: Reihenfolge der Redirects

### Vorhersage

Warum unterscheiden sich diese beiden Zeilen?

```bash
cat does-not-exist.txt 2>&1 > order-a.txt
cat does-not-exist.txt > order-b.txt 2>&1
```

```bash
echo "order-a:"
cat order-a.txt

echo "order-b:"
cat order-b.txt
```

## Erklärungspunkt

Redirects werden von links nach rechts ausgewertet. `2>&1` bedeutet: stderr zeigt ab jetzt dorthin, wohin stdout in diesem Moment zeigt.

## Experiment 8: stdin aus Datei

```bash
grep alpha < words.txt
```

## Cleanup

```bash
cd ..
rm -rf kapitel-05-pipes
```

## Nächstes Kapitel

Weiter mit [`06-skripte-startup-path-source.md`](06-skripte-startup-path-source.md).
