# Homework 05: Pipes und Redirects

1. Erzeuge eine Datei mit mehreren Zeilen.
2. Filtere sie mit `grep`.
3. Schreibe stdout und stderr in getrennte Dateien.
4. Schreibe stdout und stderr in dieselbe Datei.
5. Erkläre den Unterschied zwischen `cmd 2>&1 >file` und `cmd >file 2>&1`.

Startpunkt:

```bash
mkdir -p hw-05-pipes
cd hw-05-pipes
printf 'red\ngreen\nblue\nred blue\n' > colors.txt
```

Cleanup:

```bash
cd ..
rm -rf hw-05-pipes
```
