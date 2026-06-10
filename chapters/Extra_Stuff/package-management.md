# Extra: Paketverwaltung – apt, brew

## apt (Debian, Ubuntu)

```bash
# Paketlisten aktualisieren
sudo apt update

# Paket installieren
sudo apt install curl

# Paket entfernen
sudo apt remove curl

# Alle Pakete aktualisieren
sudo apt upgrade

# Nach einem Paket suchen
apt search jq

# Info zu einem Paket
apt show jq
```

## Homebrew (macOS)

```bash
# Paket installieren
brew install jq

# Paket entfernen
brew uninstall jq

# Alle Pakete aktualisieren
brew update && brew upgrade

# Nach Paketen suchen
brew search httpie

# Installierte Pakete auflisten
brew list
```

## Wo liegen Logs auf dem System?

| Pfad | Inhalt |
|---|---|
| `/var/log/syslog` | Allgemeines System-Log (Debian/Ubuntu) |
| `/var/log/auth.log` | Authentifizierungs-Events (Login, sudo) |
| `/var/log/nginx/` | Nginx-Logs |
| `/var/log/apt/` | apt-Installationsprotokolle |
| `journalctl` | Alle systemd-Logs (Linux mit systemd) |
| `/var/log/system.log` | System-Log auf macOS |

## Beobachten

Paketmanager sind kein Bash-Konzept, aber im täglichen Umgang mit der Shell unvermeidlich. Das Prinzip ist immer gleich: Quellen aktualisieren, dann installieren.
