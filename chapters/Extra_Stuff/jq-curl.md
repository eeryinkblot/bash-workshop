# Extra: jq und curl – JSON und HTTP auf der Kommandozeile

## curl – HTTP-Anfragen stellen

```bash
# Einfacher GET-Request
curl https://httpbin.org/get

# Response-Headers anzeigen
curl -I https://httpbin.org/get

# Nur Response-Body (kein Fortschrittsbalken)
curl -s https://httpbin.org/get

# POST-Request mit JSON
curl -s -X POST \
  -H "Content-Type: application/json" \
  -d '{"key":"value"}' \
  https://httpbin.org/post

# In Datei speichern
curl -o ausgabe.json https://httpbin.org/get
```

## jq – JSON parsen und transformieren

```bash
# JSON formatiert ausgeben
echo '{"name":"Ada","age":42}' | jq .

# Einzelnes Feld
echo '{"name":"Ada","age":42}' | jq .name

# Array-Element
echo '[1,2,3]' | jq .[0]

# Alle Elemente eines Arrays
echo '[{"n":"a"},{"n":"b"}]' | jq '.[].n'

# Mit curl kombinieren
curl -s https://httpbin.org/get | jq .headers
```

## Praktisches Beispiel: GitHub API

```bash
curl -s https://api.github.com/repos/curl/curl | jq '{name, stars: .stargazers_count, lang: .language}'
```

## httpie — menschenfreundliche Alternative zu curl

```bash
# Installation: brew install httpie / apt install httpie
http GET https://httpbin.org/get
http POST https://httpbin.org/post name=Ada
```

## Beobachten

`curl | jq` ist eine der nützlichsten Pipe-Kombinationen in der Praxis. `jq` ist ein vollständiges Abfrageformat — die Manpage lohnt sich.
