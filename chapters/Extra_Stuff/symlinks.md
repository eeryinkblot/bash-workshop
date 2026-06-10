# Extra: Links – Hardlinks und Symlinks

## Setup

```bash
mkdir -p extra-links-demo
cd extra-links-demo
echo "original" > original.txt
```

## Symlink (symbolischer Link) — ln -s

```bash
ln -s original.txt link.txt
ls -la
cat link.txt
```

```bash
# Symlink zeigt auf Ziel
ls -la link.txt
```

Zeigt: `link.txt -> original.txt`

```bash
# Was passiert, wenn das Ziel gelöscht wird?
rm original.txt
cat link.txt
```

## Beobachten

Ein Symlink ist nur ein Zeiger. Wenn das Ziel verschwindet, wird der Symlink "dangling" (kaputt). `ls -la` zeigt ihn dann in Rot.

## Hardlink — ln (ohne -s)

```bash
echo "original" > datei.txt
ln datei.txt hardlink.txt
ls -la datei.txt hardlink.txt
```

```bash
# Inode-Nummer ist identisch
ls -li datei.txt hardlink.txt
```

```bash
# Ziel löschen — Hardlink bleibt
rm datei.txt
cat hardlink.txt
```

## Beobachten

Ein Hardlink ist ein zweiter Name für dieselbe Datei (denselben Inode). Die Daten bleiben solange erhalten, wie mindestens ein Name existiert.

## Unterschied

| | Symlink | Hardlink |
|---|---|---|
| Zeigt auf | Pfad | Inode (Dateiinhalt) |
| Über Dateisystemgrenzen | Ja | Nein |
| Ziel gelöscht → | Dangling | Inhalt bleibt |
| Verzeichnisse | Ja | Nein (normalerweise) |

## Cleanup

```bash
cd ..
rm -rf extra-links-demo
```
