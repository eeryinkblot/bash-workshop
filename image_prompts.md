# Image Prompts (GPT Image 2.0)

Vorlagen für visuelle Unterstützung der Workshop-Kapitel. Alle Prompts sind für ChatGPT Images 2.0 / gpt-image-1 optimiert.

---

## 1. Pipes und Redirects — Die drei Streams
**Kapitel:** `05-pipes-und-redirects.md`

Create a technical diagram titled "stdin, stdout, stderr" for software developers learning Bash.

Show three horizontal streams as colored lines flowing left to right: stdin (file descriptor 0, blue), stdout (file descriptor 1, green), stderr (file descriptor 2, red). Show two processes as simple rounded rectangles labeled "Process A" and "Process B". Illustrate a pipe connecting stdout of Process A to stdin of Process B as a green arrow. Show stdout redirected to a file labeled "out.txt" with a green arrow. Show stderr redirected separately to a file labeled "err.txt" with a red arrow. Show the redirect operator "2>&1" as a labeled merge point where the red line joins the green line before hitting a file.

Style: flat design, white background, minimal strokes, consistent line weight, readable sans-serif labels, high contrast, ample white space. No decorative elements, no shadows, no 3D effects, no tiny text.

---

## 2. Mentales Modell — Was Bash vor dem Programm macht
**Kapitel:** `01-mental-model.md`

Create a horizontal flow diagram titled "Bash verarbeitet die Zeile" for Bash beginners.

Show a left-to-right sequence of five labeled boxes connected by arrows: (1) "Eingabe" showing the text `ls *`, (2) "Glob-Expansion" showing `ls file1 file2 file3`, (3) "Wortaufteilung", (4) "Befehlssuche" showing a magnifying glass icon, (5) "Programm startet" showing `ls`. Highlight box (1) and (5) in a different color to distinguish user input from program execution. Add a label below the arrow between box (1) and (5): "Erst Bash — dann Programm".

Style: flat design, white background, each box a soft pastel fill, bold readable labels, left-to-right flow, no decorative clutter, no shadows, no tiny text.

---

## 3. Variablen und export — Prozessvererbung
**Kapitel:** `03-variablen.md`

Create a diagram titled "export: Welche Variablen sieht ein Kind-Prozess?" for developers learning Bash variable scoping.

Show two nested rounded rectangles. The outer rectangle is labeled "Parent Shell". Inside it, list two variables: `NAME="Ada"` (marked "nicht exportiert", grey) and `export PORT=3000` (marked "exportiert", green with an export-arrow icon). The inner rectangle is labeled "Child Process (z.B. npm start)" and sits inside the parent. Inside the child, show only `PORT=3000` visible (green), and `NAME` crossed out or absent with a label "nicht sichtbar". Draw a downward green arrow from `export PORT=3000` in the parent to `PORT=3000` in the child, labeled "vererbt". Draw a red X or dashed line from `NAME` showing it does not pass through.

Style: flat design, white background, two-tone nested rectangles, clear labels in readable sans-serif, minimal icons, high contrast, no decorative elements.

---

## 4. Rechte — Das rwx-Raster
**Kapitel:** `11-rechte.md`

Create an infographic titled "Unix-Dateirechte lesen" for developers new to Linux.

Show a large monospace string "-rwxr-xr--" at the top, with each character in its own highlighted cell. Below, draw a 3×3 grid with columns labeled "user (u)", "group (g)", "others (o)" and rows labeled "read (r) = 4", "write (w) = 2", "execute (x) = 1". Fill the grid cells with checkmarks or colored dots to match the example string. Below the grid, show the octal calculation: user=7 (4+2+1), group=5 (4+0+1), others=4 (4+0+0), resulting in "chmod 754". Add a small legend row showing common patterns: 644 = "Datei", 755 = "Skript/Verzeichnis", 600 = "privater Schlüssel".

Style: flat design, white background, grid lines in light grey, color coding per column (blue=user, orange=group, green=others), bold monospace font for the permission string, readable sans-serif everywhere else, no decorative elements.

---

## 5. Prozesse — Jobkontrolle Zustandsdiagramm
**Kapitel:** `12-prozesse.md`

Create a state diagram titled "Jobkontrolle in Bash" for developers learning process management.

Show four states as rounded rectangles: "Vordergrund (running)", "Gestoppt (paused)", "Hintergrund (running)", "Beendet". Draw labeled directed arrows between them: from "Vordergrund" to "Gestoppt" labeled "Ctrl+Z", from "Gestoppt" to "Hintergrund" labeled "bg", from "Gestoppt" to "Vordergrund" labeled "fg", from "Hintergrund" to "Vordergrund" labeled "fg", from "Vordergrund" to "Beendet" labeled "Ctrl+C", from any state to "Beendet" labeled "kill". Add a starting arrow from outside into "Vordergrund" labeled "Befehl starten" and a separate entry into "Hintergrund" labeled "Befehl &".

Style: flat design, white background, each state a distinct pastel color, bold arrow labels in readable sans-serif, top-to-bottom or left-to-right layout, no decorative elements, no shadows.

---

## 6. Entrypoint-Script — Ablauf-Flowchart
**Kapitel:** `15-entrypoint-script.md`

Create a flowchart titled "entrypoint.sh — Ablauf" for developers working with Docker.

Show a top-to-bottom flow: (1) rounded start box "Container startet", (2) rectangle "set -euo pipefail", (3) diamond decision "DATABASE_URL gesetzt?" with "Nein" arrow to a red error box "Fehler: Variable fehlt → exit 1" and "Ja" arrow continuing, (4) diamond "PORT gesetzt?" same pattern, (5) rectangle "Warte auf Datenbank (until loop)", (6) diamond "Erreichbar?" with "Nein" arrow looping back to (5) and a timeout arrow to error box "Timeout → exit 1", "Ja" continues, (7) rectangle "exec \"$@\" — Anwendung starten", (8) rounded end box "Prozess läuft". Color error paths red, happy path green.

Style: flat design, white background, diamonds for decisions, rectangles for actions, rounded rectangles for start/end, monospace font for code snippets inside boxes, readable sans-serif for labels, clear directional arrows with labels, no decorative elements.
