# Workshop-Ablauf

Dies ist der Einstiegspunkt für den Workshop. Die eigentlichen Arbeitsblätter liegen kapitelweise unter `chapters/`.

## Grundregel

Kopiere Codeblöcke aus den Kapiteldateien in dein Terminal. Vor jedem Block kurz überlegen:

> Was glaube ich, was gleich passiert?

Danach ausführen und Ausgabe besprechen.

## Ablauf für einen halben Tag

| Reihenfolge | Kapitel | Thema | Zeit |
|---:|---|---|---:|
| 0 | [`chapters/00-umgebung.md`](chapters/00-umgebung.md) | Umgebung prüfen | 10 min |
| 1 | [`chapters/01-mental-model.md`](chapters/01-mental-model.md) | Was macht Bash? | 15 min |
| 2 | [`chapters/02-globbing-und-quoting.md`](chapters/02-globbing-und-quoting.md) | Globbing und Quoting | 35 min |
| 3 | [`chapters/03-variablen.md`](chapters/03-variablen.md) | Variablen, Export, Arrays | 35 min |
| 4 | [`chapters/04-funktionen-und-befehle.md`](chapters/04-funktionen-und-befehle.md) | Funktionen, Builtins, Aliases, Programme | 35 min |
| 5 | [`chapters/05-pipes-und-redirects.md`](chapters/05-pipes-und-redirects.md) | Pipes, Redirects, stdout/stderr | 45 min |
| 6 | [`chapters/06-skripte-startup-path-source.md`](chapters/06-skripte-startup-path-source.md) | Skripte, Shebang, PATH, `source` | 45 min |

## Ablauf für einen ganzen Tag

Nach Kapitel 6 zusätzlich:

| Reihenfolge | Kapitel | Thema | Zeit |
|---:|---|---|---:|
| 7 | [`chapters/07-command-substitution-exit-codes-tests.md`](chapters/07-command-substitution-exit-codes-tests.md) | Command Substitution, Exit Codes, Tests | 45 min |
| 8 | [`chapters/08-loops-und-abschluss-script.md`](chapters/08-loops-und-abschluss-script.md) | Loops und Abschluss-Script | 45 min |

## Ablauf für 90 Minuten – Systemüberblick

Kompaktes Modul: Dateien, Rechte, Prozesse, Shell-Produktivität.

| Reihenfolge | Kapitel | Thema | Zeit |
|---:|---|---|---:|
| 9 | [`chapters/09-werkzeuge.md`](chapters/09-werkzeuge.md) | man, cat, less, head, tail, wc, sort, tee | 20 min |
| 10 | [`chapters/10-dateiverwaltung.md`](chapters/10-dateiverwaltung.md) | cp, mv, rm, mkdir, Backslash-Fortsetzung | 15 min |
| 11 | [`chapters/11-rechte.md`](chapters/11-rechte.md) | chmod, chown, ls -l, Eigentümer | 20 min |
| 12 | [`chapters/12-prozesse.md`](chapters/12-prozesse.md) | ps, kill, Ctrl+Z, fg/bg/jobs | 20 min |
| 13 | [`chapters/13-history-prompt-verkettung.md`](chapters/13-history-prompt-verkettung.md) | History, PS1, &&/\|\|/;, set -euo pipefail | 15 min |

## Extra-Material

Themen für Neugierige oder als Aufhänger für Diskussionen – kein Pflichtprogramm:

- [`chapters/Extra_Stuff/systemd.md`](chapters/Extra_Stuff/systemd.md) — systemctl, journalctl
- [`chapters/Extra_Stuff/package-management.md`](chapters/Extra_Stuff/package-management.md) — apt, brew, Log-Pfade
- [`chapters/Extra_Stuff/ssh.md`](chapters/Extra_Stuff/ssh.md) — SSH, Schlüsselpaare, ~/.ssh
- [`chapters/Extra_Stuff/jq-curl.md`](chapters/Extra_Stuff/jq-curl.md) — curl, jq, httpie
- [`chapters/Extra_Stuff/symlinks.md`](chapters/Extra_Stuff/symlinks.md) — ln, Hardlinks, Symlinks
- [`chapters/Extra_Stuff/prozesssubstitution.md`](chapters/Extra_Stuff/prozesssubstitution.md) — `<()` und `>()`
- [`chapters/Extra_Stuff/shellcheck.md`](chapters/Extra_Stuff/shellcheck.md) — statische Skriptprüfung
- [`chapters/Extra_Stuff/container-cicd.md`](chapters/Extra_Stuff/container-cicd.md) — Docker, Volumes, Bash in CI
- [`chapters/Extra_Stuff/unix-geschichte.md`](chapters/Extra_Stuff/unix-geschichte.md) — UNIX-Geschichte, Philosophie, Dateisystembaum

## Homework

Optionale Aufgaben sind nach Kapiteln getrennt:

- Überblick: [`HOMEWORK.md`](HOMEWORK.md)
- Dateien: [`homework/`](homework/)

## Trainer-Material

Trainer-Notizen sind ebenfalls nach Kapiteln getrennt:

- [`trainer-notes/`](trainer-notes/)

## Folien

Die Folien sind nur Taktgeber, nicht der Ort für Code:

- [`slides/SLIDES.md`](slides/SLIDES.md)
