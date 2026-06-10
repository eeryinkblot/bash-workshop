# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Was dieses Repo ist

Ein live-geführter Bash-Workshop als reines Markdown-Repo. Es gibt keine `.sh`-Dateien, kein Build-System und kein Makefile. Alle Befehle stehen als kopierbare Codeblöcke in den Kapitel-Dateien unter `chapters/`.

## Kapitelformat

Jedes Kapitel folgt diesem Aufbau – in dieser Reihenfolge:

1. **Ziel** — ein Satz, was die Teilnehmenden danach verstehen
2. **Leitfrage** (optional) — eine Vorhersagefrage vor dem ersten Experiment
3. **Setup** — `mkdir -p kapitel-NN-name && cd kapitel-NN-name` + Testdaten erzeugen
4. **Experimente** — nummeriert, je mit optionalem **Vorhersage**-Block, Codeblock, **Beobachten**-Block
5. **Merksatz** — eine kurze, einprägsame Kernerkenntnis
6. **Cleanup** — `cd .. && rm -rf kapitel-NN-name`
7. **Nächstes Kapitel** — Link zur Folgedatei

Das didaktische Prinzip ist immer: erst vorhersagen, dann ausführen, dann beobachten, zuletzt erklären. Erklärungen kommen nicht vor dem Experiment.

## Gespiegelte Verzeichnisstruktur

Kapitel 00–08 haben je eine Datei in vier Verzeichnissen mit identischem Namensmuster:

| Verzeichnis | Zweck |
|---|---|
| `chapters/` | Teilnehmendenmaterial (Pflichtpfad im Workshop) |
| `homework/` | Optionale Vertiefungsaufgaben nach dem Workshop |
| `trainer-notes/` | Hinweise zur Moderation, Stolperstellen, Timing |
| `slides/SLIDES.md` | Foliengliederung; Code steht nie auf den Folien |

Neue Kapitel sollten in allen vier Orten angelegt werden.

## Session-Varianten und WORKSHOP.md

`WORKSHOP.md` ist der Einstiegspunkt für Teilnehmende und definiert drei Session-Varianten:

- **Halber Tag** (00–06, ~220 min)
- **Ganzer Tag** (00–08, ~310 min)
- **90 Minuten – Systemüberblick** (09–13)

Wenn Kapitel hinzukommen, wird `WORKSHOP.md` mit Zeitangabe in der passenden Tabelle ergänzt.

## Extra_Stuff

`chapters/Extra_Stuff/` enthält Themen, die nicht zum Pflichtprogramm gehören: systemd, SSH, jq/curl, Container/CI, Symlinks, Prozesssubstitution, shellcheck, Unix-Geschichte. Diese Dateien folgen keinem streng didaktischen Kapitelformat – sie sind Referenz und Gesprächsaufhänger.

## Wunschliste neuer Themen

`chapters/ADD` ist die laufende Wunschliste für neue Kapitelideen (Freitext). Themen, die darin stehen und noch nicht in 00–13 oder Extra_Stuff abgedeckt sind, sind Kandidaten für neue Kapitel.

## Sprache

Alle Inhalte sind auf Deutsch. Dateinamen, Variablennamen in Codeblöcken und technische Begriffe bleiben Englisch oder Bash-idiomatisch.
