# Homework 02: Globbing und Quoting

1. Erzeuge mehrere Dateien mit ähnlichen Namen.
2. Schreibe Globs, die genau eine, mehrere oder keine Datei matchen.
3. Vergleiche `*`, `?`, `[abc]` und `[a-z]`.
4. Erkläre in eigenen Worten, warum Globs keine Regexes sind.

Startpunkt:

```bash
mkdir -p hw-02-globs
cd hw-02-globs
touch file1 file2 file10 data.csv data.txt .hidden
```

Cleanup:

```bash
cd ..
rm -rf hw-02-globs
```
