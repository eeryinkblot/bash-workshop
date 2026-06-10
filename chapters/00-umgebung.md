# Kapitel 00: Umgebung prüfen

## Ziel

Alle arbeiten in einer Bash und in einem eigenen Arbeitsordner. Dadurch sind die Ausgaben vergleichbarer und Cleanup ist einfach.

## Vorhersage

Was erwartest du bei `echo "$BASH_VERSION"`? Gibt deine Shell dort etwas aus?

## Ausführen

```bash
bash --version
echo "$BASH_VERSION"
echo "$SHELL"
pwd
```

## Beobachten

- Gibt `BASH_VERSION` etwas aus?
- Ist deine Login-Shell wirklich Bash oder startest du Bash nur innerhalb einer anderen Shell?
- In welchem Verzeichnis befindest du dich?

## Arbeitsordner anlegen

```bash
mkdir -p bash-workshop-work
cd bash-workshop-work
pwd
```

## Sicherheitsregel für den Workshop

Wir arbeiten nur innerhalb dieses Ordners. Wenn etwas schiefgeht, kann der ganze Ordner gelöscht werden.

## Cleanup für dieses Kapitel

Noch kein Cleanup nötig. Der Ordner wird in den nächsten Kapiteln weiterverwendet.

## Nächstes Kapitel

Weiter mit [`01-mental-model.md`](01-mental-model.md).
