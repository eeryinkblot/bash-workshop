# Extra: shellcheck – Skripte statisch prüfen

## Was ist shellcheck?

shellcheck ist ein statischer Analysator für Shell-Skripte. Er findet häufige Fehler, die Bash schweigend falsch ausführt.

## Installation

```bash
# macOS
brew install shellcheck

# Debian/Ubuntu
sudo apt install shellcheck
```

## Einfaches Beispiel

Skript mit versteckten Fehlern:

```bash
cat > schlecht.sh <<'EOF'
#!/bin/bash
for f in $(ls *.txt); do
  echo "Datei: $f"
done

if [ $1 == "test" ]; then
  echo ok
fi
EOF
```

```bash
shellcheck schlecht.sh
```

## Was shellcheck meldet

| Fehler | Problem | Besser |
|---|---|---|
| `$(ls *.txt)` | Wortaufspaltung bei Leerzeichen in Dateinamen | `for f in *.txt` |
| `[ $1 == "test" ]` | Fehler wenn $1 leer ist | `[[ "$1" == "test" ]]` |
| Fehlende Quotes | Globbing/Wortaufspaltung | `"$variable"` |

## shellcheck in CI

```yaml
# GitHub Actions Beispiel
- name: shellcheck
  run: shellcheck scripts/*.sh
```

## Beobachten

shellcheck gibt zu jedem Fund eine SC-Nummer und einen Link zur Erklärung (z.B. `SC2045`). Es gibt keine false positives zu erfinden — jeder Fund lohnt sich anzuschauen.

Ein Skript das `shellcheck` fehlerfrei passiert, ist kein Beweis für Korrektheit, aber ein guter Filter gegen die häufigsten Fallen.
