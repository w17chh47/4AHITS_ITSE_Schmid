| Name          | Klasse | Fach         | Thema   | Datum      | Lehrkraft     |
| ------------- | ------ | ------------ | ------- | ---------- | ------------- |
| Cedric Schmid | 4AHITS | ITSE-Übungen | Netscan | 06.10.2025 | Franz Matejka |

## Netscan

### Übung (ping)

#### Allgemein

Der ping-Dienst verwendet den ICMP-Protokoll (Internet Control Message Protocol) auf der Netzwerkebene (Layer 3) des OSI-Modells.

Firewalls können mit ping-Requests auf verschiedene Weise umgehen:

- ICMP-Blocking: Einige Firewalls blockieren ICMP-Echo-Requests komplett, um Angriffe zu verhindern.
- Rate Limiting: Andere Firewalls begrenzen die Anzahl der ICMP-Echo-Requests, die innerhalb eines bestimmten Zeitraums empfangen werden dürfen.
- ICMP-Filterung: Einige Firewalls filtern ICMP-Echo-Requests basierend auf der Quell-IP-Adresse, der Ziel-IP-Adresse oder anderen Kriterien.

#### Cheatsheet

Send ICMP ECHO_REQUEST packets to network hosts.
More information: <https://manned.org/ping>.

Ping host:

  `ping host`

Ping a host only a specific number of times:

  `ping -c count host`

Ping host, specifying the interval in seconds between requests (default is 1 second):

  `ping -i seconds host`

Ping host without trying to lookup symbolic names for addresses:

  `ping -n host`

Ping host and ring the bell when a packet is received (if your terminal supports it):

  `ping -a host`

Also display a message if no response was received:

  `ping -O host`

Ping a host with specific number of pings, per-packet response timeout (`-W`), and total time limit (`-w`) of the entire ping run:

  `ping -c count -W seconds -w seconds host`

### Übung (ping script)

```bash
#!/bin/bash

for ((i = 1; i <= 254; i++)); do
  if ping -c 1 192.168.2.$i > /dev/null 2>&1; then
    echo "192.168.2.$i ist online"
  fi
done
```
