# Extra: Prozesssubstitution – <() und >()

## Was ist das?

Prozesssubstitution lässt einen Befehl so aussehen wie eine Datei. Bash führt den Befehl in einer Sub-Shell aus und stellt das Ergebnis über einen temporären Dateideskriptor bereit.

## Setup

```bash
mkdir -p extra-procsubst
cd extra-procsubst
printf 'alpha\nbeta\ngamma\n' > a.txt
printf 'beta\ngamma\ndelta\n' > b.txt
```

## Experiment 1: diff auf Befehlsausgaben

Zwei sortierte Ausgaben vergleichen, ohne Zwischendateien:

```bash
diff <(sort a.txt) <(sort b.txt)
```

Ohne Prozesssubstitution wäre das:

```bash
sort a.txt > tmp1.txt
sort b.txt > tmp2.txt
diff tmp1.txt tmp2.txt
rm tmp1.txt tmp2.txt
```

## Experiment 2: while read mit einer Pipe

Das geht nicht wie erwartet (Variable lebt in Sub-Shell):

```bash
count=0
cat a.txt | while read line; do
  count=$((count + 1))
done
echo "count: $count"
```

Mit Prozesssubstitution:

```bash
count=0
while read line; do
  count=$((count + 1))
done < <(cat a.txt)
echo "count: $count"
```

## Beobachten

`<(befehl)` erzeugt einen Dateideskriptor, der wie eine Datei gelesen werden kann. `>(befehl)` tut dasselbe für das Schreiben. Das ist Bash-spezifisch und nicht POSIX.

## Cleanup

```bash
cd ..
rm -rf extra-procsubst
```
