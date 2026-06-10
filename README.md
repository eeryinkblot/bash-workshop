# Bash Workshop Markdown-only, kapitelweise

Dieses Repo enthält einen live-geführten Bash-Workshop als Markdown-Material.

Die Struktur ist bewusst **kapitelweise** und **Markdown-only**:

- keine `.sh`-Dateien
- kein `Makefile`
- keine vorbereiteten Lab-Skripte
- alle Befehle stehen als kopierbare Codeblöcke in Markdown-Dateien
- jedes Kapitel hat eine eigene Teilnehmerdatei
- Homework und Trainer-Notizen sind ebenfalls nach Kapiteln getrennt

## Start für Teilnehmende

Öffne zuerst:

```text
WORKSHOP.md
```

Dort ist die Reihenfolge festgelegt. Von dort springst du in die einzelnen Kapitel unter `chapters/`.

## Empfohlene Vorbereitung

```bash
bash --version
mkdir -p bash-workshop-work
cd bash-workshop-work
pwd
```

Die Codeblöcke enthalten bewusst kein führendes `$`, damit sie direkt kopiert werden können.

## Dateien und Ordner

```text
bash-workshop-md-chapters/
├── README.md
├── WORKSHOP.md
├── HOMEWORK.md
├── ATTRIBUTION.md
├── chapters/
│   ├── 00-umgebung.md
│   ├── 01-mental-model.md
│   ├── 02-globbing-und-quoting.md
│   ├── 03-variablen.md
│   ├── 04-funktionen-und-befehle.md
│   ├── 05-pipes-und-redirects.md
│   ├── 06-skripte-startup-path-source.md
│   ├── 07-command-substitution-exit-codes-tests.md
│   └── 08-loops-und-abschluss-script.md
├── homework/
├── trainer-notes/
├── slides/
└── reference/
```

## Workshop-Prinzip

Pro Kapitel:

1. Vorhersage: Was erwartest du?
2. Codeblock kopieren und ausführen.
3. Ausgabe beobachten.
4. Erklärung im Live-Workshop.
5. Optional: Homework später.

Die Markdown-Dateien sind kein Ersatz für den Live-Workshop. Sie sind die Arbeitsunterlage, damit im Workshop keine Zeit durch Abtippen verloren geht.
