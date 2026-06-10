# Kapitel 15: Entrypoint-Script

## Ziel

Du schreibst ein vollständiges, robustes Entrypoint-Script, wie es in Docker-Containern eingesetzt wird. Alle Konzepte aus dem Workshop fließen zusammen.

## Was ist ein Entrypoint?

Ein Entrypoint ist das erste Skript, das beim Start eines Containers läuft. Es prüft die Konfiguration, wartet ggf. auf Abhängigkeiten und startet dann die eigentliche Anwendung.

## Setup

```bash
mkdir -p kapitel-15-entrypoint
cd kapitel-15-entrypoint
```

## Experiment 1: Pflichtumgebungsvariablen prüfen

```bash
cat > check-env.sh <<'EOF'
#!/usr/bin/env bash
set -euo pipefail

: "${DATABASE_URL:?DATABASE_URL muss gesetzt sein}"
: "${PORT:?PORT muss gesetzt sein}"

echo "Konfiguration OK: PORT=$PORT"
EOF

chmod +x check-env.sh
```

Ohne Variablen:

```bash
bash check-env.sh
```

Mit Variablen:

```bash
DATABASE_URL=postgres://localhost/dev PORT=3000 bash check-env.sh
```

## Beobachten

`${VAR:?Meldung}` ist Bash-Syntax: wenn `VAR` leer oder ungesetzt ist, bricht das Skript mit der Meldung ab. `set -u` allein gibt eine weniger lesbare Fehlermeldung. Das `:` ist ein Builtin, das nichts tut — es wertet aber die Expansion aus.

## Experiment 2: Auf eine Abhängigkeit warten

```bash
cat > wait-for.sh <<'EOF'
#!/usr/bin/env bash
set -euo pipefail

HOST="${1:?Hostname fehlt}"
PORT="${2:?Port fehlt}"
TIMEOUT="${3:-30}"

echo "Warte auf $HOST:$PORT (max ${TIMEOUT}s)..."

elapsed=0
until bash -c "echo > /dev/tcp/$HOST/$PORT" 2>/dev/null; do
  if [[ "$elapsed" -ge "$TIMEOUT" ]]; then
    echo "Timeout: $HOST:$PORT nicht erreichbar nach ${TIMEOUT}s" >&2
    exit 1
  fi
  sleep 1
  elapsed=$((elapsed + 1))
done

echo "$HOST:$PORT ist erreichbar"
EOF

chmod +x wait-for.sh
```

```bash
bash wait-for.sh localhost 80 3
```

## Beobachten

`until` läuft, solange der Befehl *fehlschlägt*. `/dev/tcp/host/port` ist eine Bash-spezifische Abkürzung für TCP-Verbindungstest. `>&2` schreibt Fehlermeldungen auf stderr, wie erwartet.

## Experiment 3: Das vollständige Entrypoint-Script

```bash
cat > entrypoint.sh <<'EOF'
#!/usr/bin/env bash
set -euo pipefail

# Pflichtumgebungsvariablen
: "${DATABASE_URL:?DATABASE_URL muss gesetzt sein}"
: "${PORT:?PORT muss gesetzt sein}"

DB_HOST="${DB_HOST:-localhost}"
DB_PORT="${DB_PORT:-5432}"

echo "Starte Container..."
echo "  PORT=$PORT"
echo "  DB=$DB_HOST:$DB_PORT"

# Auf Datenbank warten
echo "Warte auf Datenbank..."
elapsed=0
until bash -c "echo > /dev/tcp/$DB_HOST/$DB_PORT" 2>/dev/null; do
  if [[ "$elapsed" -ge 30 ]]; then
    echo "Fehler: Datenbank nicht erreichbar" >&2
    exit 1
  fi
  sleep 1
  elapsed=$((elapsed + 1))
done
echo "Datenbank erreichbar."

# Anwendung starten — exec ersetzt diesen Prozess
exec "$@"
EOF

chmod +x entrypoint.sh
```

Skript prüfen (ohne laufende DB):

```bash
DATABASE_URL=postgres://localhost/dev PORT=3000 bash entrypoint.sh echo "würde jetzt starten"
```

## Beobachten

`exec "$@"` ist das letzte Statement: es ersetzt den Shell-Prozess durch den übergebenen Befehl. Damit hat der gestartete Prozess PID 1 im Container und empfängt Signale (SIGTERM beim `docker stop`) direkt — ohne dieses Muster würde die Shell die Signale abfangen und die Anwendung würde nicht sauber beendet.

## Was dieses Skript nutzt

| Konzept | Kapitel |
|---|---|
| `#!/usr/bin/env bash` + `set -euo pipefail` | 06, 13 |
| `${VAR:?}` Pflichtprüfung | 03 |
| `${VAR:-default}` Fallback | 03 |
| `until`-Schleife | 08 |
| `[[ ]]` Test + `-ge` | 07 |
| `>&2` stderr | 05 |
| `exec "$@"` | 04, 06 |
| `exit 1` | 07 |

## Cleanup

```bash
cd ..
rm -rf kapitel-15-entrypoint
```
