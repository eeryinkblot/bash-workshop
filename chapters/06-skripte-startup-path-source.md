# Kapitel 06: Skripte, Shebang, PATH und source

## Ziel

Du verstehst, wie Bash-Skripte gestartet werden, was die Shebang-Zeile macht, welche Rolle `PATH` spielt und was `source` anders macht.

## Setup

```bash
mkdir -p kapitel-06-skripte
cd kapitel-06-skripte
```

## Experiment 1: Skript als Datei erzeugen

```bash
cat > simple-script <<'EOF'
#!/usr/bin/env bash
echo "Ich bin ein Skript"
EOF

cat simple-script
```

## Experiment 2: Direkt ausführen

### Vorhersage

Was passiert ohne Execute-Bit?

```bash
./simple-script
```

Jetzt ausführbar machen:

```bash
chmod +x simple-script
./simple-script
```

## Experiment 3: Ohne `./` ausführen

```bash
simple-script
```

## Beobachten

Bash sucht Befehle in den Verzeichnissen aus `PATH`, nicht automatisch im aktuellen Verzeichnis.

## Experiment 4: PATH ansehen

```bash
echo "$PATH"
printf '%s\n' ${PATH//:/\n}
```

## Experiment 5: Aktuelles Verzeichnis temporär in PATH aufnehmen

```bash
PATH="$PATH:$PWD"
simple-script
```

## Hinweis

Das aktuelle Verzeichnis dauerhaft in `PATH` aufzunehmen ist oft keine gute Idee. Für den Workshop ist es ein kontrolliertes Experiment.

## Experiment 6: `source`

```bash
cat > set-var-demo <<'EOF'
MY_SOURCED_VAR="gesetzt durch Datei"
echo "Datei wurde ausgeführt"
EOF

bash set-var-demo
echo "Nach bash: <$MY_SOURCED_VAR>"

source set-var-demo
echo "Nach source: <$MY_SOURCED_VAR>"
```

## Beobachten

`bash datei` startet einen neuen Bash-Prozess. `source datei` führt die Datei in der aktuellen Shell aus.

## Experiment 7: Startup-Dateien nur ansehen

Diese Dateien können auf deinem System existieren oder nicht:

```bash
ls -la ~/.bashrc ~/.bash_profile ~/.profile 2>/dev/null || true
```

Nicht blind ändern. Nur ansehen:

```bash
for f in ~/.bashrc ~/.bash_profile ~/.profile; do
  if [[ -f "$f" ]]; then
    echo "--- $f ---"
    head -n 20 "$f"
  fi
done
```

## Cleanup

```bash
cd ..
rm -rf kapitel-06-skripte
unset MY_SOURCED_VAR
```

## Nächstes Kapitel

Für den Ganztagsworkshop weiter mit [`07-command-substitution-exit-codes-tests.md`](07-command-substitution-exit-codes-tests.md).
