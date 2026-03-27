# IPwhitelist

Ein Bash-Skript, das die öffentliche IP-Adresse des aktuellen Hosts ermittelt und darauf basierend eingehende Hetzner Cloud Firewall-Regeln aktualisiert. Ziel ist es, definierte Ports/Protokolle (z. B. 22/tcp, 80/tcp, 443/tcp oder icmp) nur von deiner aktuellen Public IP zu erlauben – ideal für dynamische IPs (z. B. Heimanschluss, unterwegs).

Das Skript:

- ermittelt die aktuelle öffentliche IPv4 oder IPv6 (umschaltbar)

- sucht eine Hetzner Cloud Firewall anhand ihres Namens

- ersetzt/aktualisiert Regeln gezielt über die description (statt alles blind zu überschreiben)

- installiert fehlende Abhängigkeiten (curl, jq) optional via apt

- beendet sich ohne Änderungen, wenn die Regeln bereits zur aktuellen IP passen

Typischer Use-Case: SSH/HTTP/HTTPS-Zugriff nur von deiner aktuellen IP auf Servern erlauben, ohne manuell die Firewall im Hetzner Panel anzupassen.

# "DynDNS" Updater

Bash-Script zur automatischen Aktualisierung von DNS-Einträgen bei Hetzner.

Das Script ermittelt die aktuelle öffentliche IP-Adresse (IPv4 und/oder IPv6) und aktualisiert die entsprechenden DNS-Records (A / AAAA) für definierte Subdomains nur dann, wenn sich die IP tatsächlich geändert hat.

- Unterstützung für IPv4 (A) und IPv6 (AAAA) (einzeln oder kombiniert) -> IPv6 ist ungetestet!

- Mehrere Subdomains gleichzeitig verwaltbar
```bash
SUBDOMAINS=(
  "sub1"
  "sub2"
  "sub3"
)
```

- Änderungen nur bei tatsächlicher IP-Änderung

- installiert fehlende Abhängigkeiten (curl, jq) via Pakagemanager