| Name          | Klasse | Fach         | Thema          | Datum      | Lehrkraft     |
| ------------- | ------ | ------------ | -------------- | ---------- | ------------- |
| Cedric Schmid | 4AHITS | ITSE-Übungen | Host Discovery | 06.10.2025 | Franz Matejka |

## Aufgabenstellung

Durch aktives Versenden von Netzwerkpaketen und Auswerten der Rückantwort (oder ausbleiben derselben) wird ermittelt:

1. network scanning: welche Rechner sind im Netzwerk und welche Dienste stellen diese zur Verfügung?
2. vulnerability scanning: gibt es bekannte Schwachstellen die ausgenutzt werden können?

Findet in der information gathering Phase eines Angriffs statt.

**Voraussetzungen**

für die folgenden Übungen

- VM mit Kali
- VM mit Metasploitable
- VMs im Bridged Mode (Bridge ins Labor-Netzwerk)

**Übung (ping)**

Als host discovery (host scanning) versteht man den Vorgang um unbekannte Geräte in einem Netzwerk zu finden, bzw. festzustellen ob bekannte Geräte im Netzwerk erreichbar sind.

Das einfachste Werkzeug dafür ist ping.

- Verwende Kali und Metasploitable im Bridged Mode (Bridge ins Labor-Netzwerk)
- Experimentiere mit ping im Labor-Netzwerk (Metasploitable, Default Gateway, …)
- Recherchiere zu den Optionen von ping, erstelle ein kleines Cheat Sheet
- Welchen Netzwerkdienst verwendet der ping Dienst? Recherchiere wie Firewalls häufig mit ping umgehen.

**Übung (ping script)**

Schreibe ein shell Skript das automatisiert (Schleife) alle Hosts im subnet anpingt. Die Ausgabe soll so sein, dass man daraus die aktiven Hosts erkennen kann (für nicht aktive Hosts soll keine Ausgabe sein).

Info (nmap)
Nmap: the Network Mapper - Free Security Scanner

Dieses Tool dient dazu aktive Hosts in Netzwerken zu ermitteln (Host Discovery) und diese weiters auf angebotene Dienste zu durchforsten (Port Scan). nmap erzeugt dafür eine große Menge an Netzwerk Paketen und wertet die Rückantworten aus.

Nmap (“Network Mapper”) is an open source tool for network exploration and security auditing. It was designed to rapidly scan large networks, although it works fine against single hosts.

One of Nmap’s most exciting new features is the Nmap Scripting Engine, which extends Nmap’s functionality using the simple and efficient Lua programming language. … you can also write your own

Wird gerne in Filmen verwendet wenn es um Hacking geht (Nmap In The Movies)

**Übung (host discovery)**

nmap ist ein Tool zum network scanning. In einer ersten Phase (host discovery, ping scan oder ping sweep) ermittelt nmap alle aktiven Hosts.

Aufgaben:

- Recherchiere zur grundlegenden Anwendung von nmap für einen sogenannten ping scan (host discovery).
- Ermittle alle aktiven Hosts im Subnetz des Labor-Netzwerks mit nmap.

Hinweise:

- nmap benötigt als Argument den IP Adressbereich des Subnet in Präfix Notation (z.B.: 192.168.178.0/24)
- Mit der Option -sn führt nmap nur den ping scan durch (ansonsten wird automtisch auch die nächste, länger dauernde, Phase des scans ausgeführt – siehe folgende Übung)
Creative Commons Licence – Franz Matejka – HTL Braunau

## Host Discovery

### Übung (ping)

#### Allgemein

ping verwendet das ICMP-Protokoll (Internet Control Message Protocol)

Firewalls können mit ping-Requests auf verschiedene Weise umgehen:

- ICMP-Blocking
- Rate Limiting
- ICMP-Filterung

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

### Übung (host discovery)

ping scan: `nmap -sn 192.168.0.0/24`

```bash
$ nmap -sn 10.51.181.223/24
Starting Nmap 7.92 ( https://nmap.org ) at 2025-10-13 12:36 CEST
Nmap scan report for 10.51.181.76
Host is up (0.0056s latency).
Nmap scan report for 10.51.181.223
Host is up (0.00038s latency).
Nmap done: 256 IP addresses (2 hosts up) scanned in 6.97 seconds
```
