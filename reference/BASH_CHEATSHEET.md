# Bash Cheatsheet

## Expansion und Quoting

```bash
echo *       # Bash expandiert den Glob
echo '*'     # wörtlicher Stern
echo "$HOME" # Variable wird expandiert
echo '$HOME' # wörtlicher Text
```

## Variablen

```bash
NAME="Ada"
echo "$NAME"
export NAME="Ada"
unset NAME
```

## Arrays

```bash
items=(one two three)
echo "${items[0]}"
echo "${items[@]}"
```

## Funktionen

```bash
hello() {
  echo "Hello $1"
}
hello World
```

## Exit Codes

```bash
some_command
echo "$?"
```

Konvention: `0` bedeutet Erfolg, alles andere ist je nach Programm Fehler oder Sonderfall.

## Redirects

```bash
cmd >out.txt       # stdout in Datei
cmd 2>err.txt      # stderr in Datei
cmd >all.txt 2>&1  # stdout und stderr in dieselbe Datei
cmd >>out.txt      # anhängen
cmd <input.txt     # stdin aus Datei
```

## Pipes

```bash
cat file.txt | grep pattern
```

Die Pipe verbindet stdout des linken Befehls mit stdin des rechten Befehls.
