# Extra: systemd – systemctl und journalctl

## Wann relevant

Auf Linux-Systemen (Ubuntu, Debian, RHEL, CentOS, Arch) mit systemd als Init-System. Auf macOS nicht verfügbar.

## Dienste verwalten — systemctl

```bash
# Status eines Dienstes anzeigen
systemctl status nginx

# Dienst starten / stoppen / neustarten
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl restart nginx

# Dienst beim Systemstart aktivieren / deaktivieren
sudo systemctl enable nginx
sudo systemctl disable nginx

# Alle laufenden Dienste auflisten
systemctl list-units --type=service --state=running
```

## Logs lesen — journalctl

```bash
# Alle Logs (neueste zuletzt)
journalctl

# Logs eines bestimmten Dienstes
journalctl -u nginx

# Nur die letzten 50 Zeilen
journalctl -u nginx -n 50

# Logs seit dem letzten Boot
journalctl -b

# Logs in Echtzeit verfolgen (wie tail -f)
journalctl -f

# Logs eines bestimmten Zeitraums
journalctl --since "2024-01-01" --until "2024-01-02"
```

## Beobachten

systemd ersetzt klassische init-Skripte. journalctl sammelt strukturierte Logs von allen Diensten zentral – kein `tail /var/log/nginx/error.log` nötig (obwohl das auch noch geht).
