# Extra: SSH – Sichere Verbindung zu entfernten Systemen

## Verbinden

```bash
ssh benutzername@hostname
ssh benutzername@192.168.1.10
ssh -p 2222 benutzername@hostname
```

## Schlüsselpaar erzeugen

```bash
ssh-keygen -t ed25519 -C "mein-kommentar"
```

Erzeugt:
- `~/.ssh/id_ed25519` — privater Schlüssel (niemals teilen)
- `~/.ssh/id_ed25519.pub` — öffentlicher Schlüssel (auf Server kopieren)

## Öffentlichen Schlüssel auf Server kopieren

```bash
ssh-copy-id benutzername@hostname
```

Danach funktioniert der Login ohne Passwort.

## ~/.ssh Verzeichnis

```bash
ls -la ~/.ssh
```

| Datei | Bedeutung |
|---|---|
| `id_ed25519` | Privater Schlüssel — Rechte müssen `600` sein |
| `id_ed25519.pub` | Öffentlicher Schlüssel |
| `authorized_keys` | Öffentliche Schlüssel, die sich einloggen dürfen |
| `known_hosts` | Gespeicherte Host-Fingerprints |
| `config` | SSH-Aliase und Konfigurationsoptionen |

## SSH Config (~/.ssh/config)

```
Host meinserver
    HostName 192.168.1.10
    User ubuntu
    IdentityFile ~/.ssh/id_ed25519
    Port 22
```

Danach einfach:

```bash
ssh meinserver
```

## Beobachten

SSH-Schlüssel statt Passwörter sind Standard in der Praxis. Der private Schlüssel muss `chmod 600` haben — sonst verweigert SSH die Nutzung.
