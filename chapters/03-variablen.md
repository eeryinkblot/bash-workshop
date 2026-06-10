# Kapitel 03: Variablen

## Ziel

Du verstehst einfache Bash-Variablen, Quoting, Export und erste Array-Zugriffe.

## Setup

```bash
mkdir -p kapitel-03-variablen
cd kapitel-03-variablen
```

## Experiment 1: Einfache Variable

```bash
MYSTRING=astring
echo $MYSTRING
echo "$MYSTRING"
```

## Beobachten

Die Zuweisung hat keine Leerzeichen um `=`. Mit `$` wird der Wert gelesen.

## Experiment 2: Leerzeichen und Quotes

### Vorhersage

Warum funktioniert die erste Zeile nicht wie erwartet?

```bash
MYSENTENCE=A sentence
```

Jetzt korrekt:

```bash
MYSENTENCE="A sentence"
echo "$MYSENTENCE"
```

## Experiment 3: Single Quotes vs Double Quotes

```bash
MYSTRING=astring
echo "Value: $MYSTRING"
echo 'Value: $MYSTRING'
```

## Beobachten

Double Quotes erlauben Variablenexpansion. Single Quotes machen den Inhalt wörtlich.

## Experiment 4: Globs in Variablen

```bash
touch file1 file2
MYGLOB=*
echo $MYGLOB
echo "$MYGLOB"
MYGLOB='*'
echo $MYGLOB
echo "$MYGLOB"
```

## Beobachten

Unquoted Variablenwerte können später wieder Word Splitting und Globbing auslösen. Deshalb ist `"$variable"` fast immer der richtige Default.

## Experiment 5: Export

```bash
MYLOCAL="nur in dieser Shell"
bash -c 'echo "Kindprozess sieht MYLOCAL=<$MYLOCAL>"'
export MYEXPORTED="sichtbar für Kindprozesse"
bash -c 'echo "Kindprozess sieht MYEXPORTED=<$MYEXPORTED>"'
```

## Beobachten

Nur exportierte Variablen landen in der Umgebung von Kindprozessen.

## Experiment 6: Arrays

```bash
items=(alpha beta gamma)
echo "${items[0]}"
echo "${items[1]}"
echo "${items[@]}"
echo "Anzahl: ${#items[@]}"
```

## Merksatz

Variablen immer bewusst quoten:

```bash
echo "$MYSTRING"
```

Nicht als Reflex:

```bash
echo $MYSTRING
```

## Cleanup

```bash
cd ..
rm -rf kapitel-03-variablen
unset MYSTRING MYSENTENCE MYGLOB MYLOCAL MYEXPORTED
```

## Nächstes Kapitel

Weiter mit [`04-funktionen-und-befehle.md`](04-funktionen-und-befehle.md).
