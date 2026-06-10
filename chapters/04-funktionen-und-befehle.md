# Kapitel 04: Funktionen und Befehlsarten

## Ziel

Du verstehst Bash-Funktionen und kannst unterscheiden zwischen Builtins, Funktionen, Aliases und Programmen.

## Setup

```bash
mkdir -p kapitel-04-funktionen
cd kapitel-04-funktionen
```

## Experiment 1: Eine Funktion definieren

```bash
hello() {
  echo "Hello World"
}

hello
```

## Experiment 2: Argumente

### Vorhersage

Was ist der Unterschied zwischen den beiden Aufrufen?

```bash
show_args() {
  printf '1=<%s>\n' "$1"
  printf '2=<%s>\n' "$2"
}

show_args "Hello World"
show_args Hello World
```

## Beobachten

Bash-Funktionen bekommen Argumente wie Skripte: `$1`, `$2`, ... Quotes beeinflussen, wie viele Argumente entstehen.

## Experiment 3: Variable Scope

```bash
myvar="außen"

show_var() {
  echo "in function: $myvar"
}

show_var
```

Jetzt mit `local`:

```bash
change_var() {
  local myvar="innen"
  echo "in function: $myvar"
}

change_var
echo "outside: $myvar"
```

## Experiment 4: Was ist ein Befehl?

```bash
type cd
type echo
type grep
type hello
```

## Experiment 5: Alias

```bash
alias ll='ls -l'
type ll
ll
unalias ll
```

## Experiment 6: Builtin explizit aufrufen

```bash
pwd
builtin pwd
```

## Merksatz

Wenn Bash einen Namen sieht, muss sie entscheiden, was damit gemeint ist. `type name` ist oft der schnellste Weg, das zu prüfen.

## Cleanup

```bash
cd ..
rm -rf kapitel-04-funktionen
unset -f hello show_args show_var change_var 2>/dev/null || true
unset myvar
```

## Nächstes Kapitel

Weiter mit [`05-pipes-und-redirects.md`](05-pipes-und-redirects.md).
