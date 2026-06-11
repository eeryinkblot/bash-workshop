---
marp: true
theme: gaia
paginate: true
class: lead
---

<!-- _paginate: false -->

# Bash für Docker-Developer

## 90 Minuten. Ein echtes Entrypoint-Script.

---

## Heute

1. Umgebung & mentales Modell
2. Pipes & Redirects
3. Variablen & Export
4. grep & find
5. `&&`, `||`, `set -euo pipefail`
6. **Finale: Entrypoint-Script**

---

<!-- _class: lead -->

# 00 — Umgebung

## Läuft bei dir wirklich Bash?

---

## Spielregeln

- Erst **vorhersagen**
- Dann **ausführen**
- Dann **beobachten**

Alles passiert in einem Wegwerf-Ordner.

---

<!-- _class: lead -->

# 01 — Mentales Modell

## `ls *` — wer sieht den Stern?

---

## Merksatz

> **Erst Bash, dann Programm.**

Die Überraschung passiert oft, bevor dein Programm startet.

---

<!-- _class: lead -->

# 05 — Pipes & Redirects

## Warum geht die Fehlermeldung nicht durch die Pipe?

---

## Drei Kanäle

| | |
|---|---|
| stdin | rein |
| stdout | raus |
| stderr | Fehler — **separat!** |

---

## Merksatz

> Pipe verbindet **stdout** mit **stdin**.
> stderr läuft daran vorbei.

`docker logs` lebt von genau diesem Wissen.

---

<!-- _class: lead -->

# 03 — Variablen

## Wann wird `$name` ersetzt?

---

## Zwei Welten

- `"..."` → Variable wird **expandiert**
- `'...'` → alles **wörtlich**

Und: Kindprozesse sehen nur **exportierte** Variablen.

---

## Merksatz

> `"$var"` ist der sichere Default.

`.env`, `docker run -e`, Compose — alles nur Export.

---

<!-- _class: lead -->

# 14 — grep & find

## Wo steht das? Wo liegt das?

---

## Arbeitsteilung

- `grep` → durchsucht **Inhalte**
- `find` → durchsucht **Pfade**

Zusammen: fast jede „Wo ist das?“-Frage.

---

## Merksatz

> `docker logs app | grep -i error`

Der Alltagsgriff Nummer eins.

---

<!-- _class: lead -->

# 13 — Verkettung

## Was passiert nach einem Fehler?

---

## Drei Operatoren

| | |
|---|---|
| `&&` | weiter nur bei **Erfolg** |
| `\|\|` | weiter nur bei **Fehler** |
| `;` | weiter **immer** |

---

## Merksatz

> `set -euo pipefail`

Der Sicherheitsgurt für jedes Skript.

---

<!-- _class: lead -->

# 15 — Entrypoint-Script

## Alles fließt zusammen.

---

## Das Skript kann

1. Pflicht-Variablen **prüfen**
2. Auf die Datenbank **warten**
3. Die App per `exec` **übernehmen lassen**

---

## Warum `exec "$@"`?

- App wird **PID 1**
- `docker stop` → SIGTERM kommt **an**
- Sauberer Shutdown

---

<!-- _class: lead -->

# Geschafft!

## Ihr habt ein produktionsreifes Entrypoint-Script geschrieben.

Code & Übungen: `chapters/` · Sprechtext: `slides/docker-track/sprechtext/`
