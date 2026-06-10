# Kapitel 02: Globbing und Quoting

## Ziel

Du verstehst, wann Bash Dateinamen expandiert und wie Quotes diese Expansion beeinflussen.

## Setup

```bash
mkdir -p kapitel-02-globbing
cd kapitel-02-globbing
rm -rf ./* ./.demo-hidden 2>/dev/null || true
touch file1 file2 file3 notes.txt
```

## Experiment 1: Stern-Glob

### Vorhersage

Was ist der Unterschied zwischen `ls *` und `echo *`?

```bash
ls *
echo *
```

## Beobachten

Beide Befehle bekommen nicht den Stern als Stern. Bash ersetzt `*` vorher durch passende Dateinamen.

## Experiment 2: Quotes

### Vorhersage

Was passiert mit Single Quotes und Double Quotes?

```bash
ls '*'
ls "*"
echo '*'
echo "*"
```

## Beobachten

Quotes verhindern hier Globbing. Das Programm bekommt den Stern wörtlich.

## Experiment 3: Andere Glob-Zeichen

```bash
ls file1
ls file?
ls file[12]
ls file[0-9]
ls *.txt
```

## Experiment 4: Dotfiles

```bash
touch .demo-hidden
echo *
echo .*
ls
ls -a
```

## Beobachten

Normale Globs wie `*` matchen versteckte Dateien nicht. Dafür musst du explizit mit einem Punkt beginnen oder Optionen wie `ls -a` nutzen.

## Experiment 5: Globs sind keine Regexes

```bash
touch abc axc a-c
printf '<%s>\n' a.c
printf '<%s>\n' a?c
printf '<%s>\n' a*c
```

## Beobachten

In Globs bedeutet `?` ein beliebiges einzelnes Zeichen. Der Punkt ist kein Regex-Punkt, sondern ein normaler Punkt.

## Mini-Erklärung

Globbing ist eine Bash-Expansion. Das Programm sieht normalerweise nicht das Muster, sondern die expandierte Liste von Dateinamen.

## Cleanup

```bash
cd ..
rm -rf kapitel-02-globbing
```

## Nächstes Kapitel

Weiter mit [`03-variablen.md`](03-variablen.md).
