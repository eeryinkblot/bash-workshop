# Kapitel 07: Command Substitution, Exit Codes und Tests

## Ziel

Du verstehst, wie Befehlsausgaben in andere Befehle eingesetzt werden, wie Exit Codes funktionieren und wie Tests in Bash gelesen werden.

## Setup

```bash
mkdir -p kapitel-07-tests
cd kapitel-07-tests
printf 'alpha\nbeta\ngamma\n' > words.txt
```

## Experiment 1: Command Substitution

```bash
echo "Hostname: $(hostname)"
echo 'Hostname: $(hostname)'
```

## Beobachten

In Double Quotes wird `$(...)` ausgeführt. In Single Quotes bleibt es wörtlich.

## Experiment 2: Verschachtelung

```bash
echo "Aktueller Ordner: $(basename "$(pwd)")"
```

## Experiment 3: Exit Code lesen

```bash
ls words.txt
echo "$?"
ls does-not-exist.txt
echo "$?"
```

## Beobachten

`0` bedeutet Erfolg. Nicht-null bedeutet: Das Programm signalisiert einen Sonderfall oder Fehler.

## Experiment 4: grep und Exit Codes

```bash
grep alpha words.txt
echo "grep alpha: $?"

grep delta words.txt
echo "grep delta: $?"
```

## Beobachten

Bei `grep` bedeutet Exit Code `1`: keine Zeile gefunden. Das ist kein Crash, sondern eine fachliche Antwort.

## Experiment 5: if mit einem Befehl

```bash
if grep alpha words.txt; then
  echo "alpha gefunden"
else
  echo "alpha nicht gefunden"
fi
```

```bash
if grep delta words.txt; then
  echo "delta gefunden"
else
  echo "delta nicht gefunden"
fi
```

## Experiment 6: Tests mit `[[ ... ]]`

```bash
name="Ada"

if [[ "$name" == "Ada" ]]; then
  echo "Name passt"
fi
```

Dateitest:

```bash
if [[ -f words.txt ]]; then
  echo "words.txt ist eine Datei"
fi
```

## Experiment 7: Numerische Tests

```bash
count=$(grep -c alpha words.txt)

if [[ "$count" -gt 0 ]]; then
  echo "alpha kommt mindestens einmal vor"
fi
```

## Cleanup

```bash
cd ..
rm -rf kapitel-07-tests
```

## Nächstes Kapitel

Weiter mit [`08-loops-und-abschluss-script.md`](08-loops-und-abschluss-script.md).
