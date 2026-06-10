# Kapitel 08: Loops und Abschluss-Script

## Ziel

Du schreibst einfache Schleifen und kombinierst Variablen, Quoting, Tests und Redirects in einem kleinen Skript.

## Setup

```bash
mkdir -p kapitel-08-loops
cd kapitel-08-loops
printf 'alpha\nbeta\ngamma\n' > words.txt
```

## Experiment 1: for über Wörter

```bash
for word in alpha beta gamma; do
  echo "word=<$word>"
done
```

## Experiment 2: for über Dateien

```bash
touch a.txt b.txt c.log

for file in *.txt; do
  echo "txt file: $file"
done
```

## Experiment 3: while read

```bash
while IFS= read -r line; do
  echo "line=<$line>"
done < words.txt
```

## Beobachten

`while read` ist oft die bessere Form, wenn Zeilen aus Dateien verarbeitet werden sollen.

## Abschluss-Script erzeugen

```bash
cat > count-matches <<'EOF'
#!/usr/bin/env bash

pattern=$1
file=$2

if [[ -z "$pattern" || -z "$file" ]]; then
  echo "Usage: $0 PATTERN FILE" >&2
  exit 2
fi

if [[ ! -f "$file" ]]; then
  echo "Not a file: $file" >&2
  exit 1
fi

count=$(grep -c "$pattern" "$file")

echo "Matches for '$pattern' in '$file': $count"
EOF

chmod +x count-matches
```

## Abschluss-Script ausführen

```bash
./count-matches alpha words.txt
./count-matches delta words.txt
./count-matches
./count-matches alpha does-not-exist.txt
```

## Exit Codes prüfen

```bash
./count-matches alpha words.txt
echo "$?"

./count-matches alpha does-not-exist.txt
echo "$?"
```

## Mini-Review

Welche Themen stecken im Script?

- Variablen: `$1`, `$2`, `pattern`, `file`, `count`
- Quoting: `"$pattern"`, `"$file"`
- Tests: `[[ -z ... ]]`, `[[ ! -f ... ]]`
- stderr: `>&2`
- Exit Codes: `exit 2`, `exit 1`
- Command Substitution: `$(grep -c ...)`

## Cleanup

```bash
cd ..
rm -rf kapitel-08-loops
```

## Ende

Du hast jetzt die Basis, um Bash-Skripte bewusster zu lesen, zu schreiben und zu debuggen.
