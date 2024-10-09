# KirchenCloud
Aufbaubeschreibung einer Digitalen Platform für Kirchengemeinden

In der Evangelischen Kirchengemeinde in Mühlhausen an der Würm wurde eine Digiale Platform geschaffen um Verwaltungs- und Kommunikationsprozesse zu vereinfachen.
Hierbei hat sich das verantwortliche Team für eine On-Premise Lösung mit eigener Hardware entschieden.
Im folgendem wird der Aufbau und die verwendeten Technologien beschrieben.

## Hardware
Für die Platform wurden folgende Komponenten verbaut:
- HP DL380 G9 (Server)
  - 2x Intel(R) Xeon(R) CPU E5-2680 v4
  - 64 GB RAM
  - 32 GB MicroSD Karte
  - 2x 1TB SSD im SFF Slot (ZFS RAID-1)
  - 4x 4TB Segate SAS HDD im LFF Slot (RAIDZ2)
  - HP FLOM Karte 4x Gigabit Ethernet
- Unifi Cloud Gateway Ultra
- USW 24
Zusätzlich wurde ein geeignetes Rack und sonstiges Zubehör angeschaft.

Der DL380 wurde aufgrund seines Formfaktors ausgewählt der in unserer Ausstatungsvariante 16 LFF Einschübe besitzt.
Es wurde sich für LFF Einschübe entschieden, da die LFF Festplatten in der Anschaffung einen niedrigeren Preis pro GB haben als die SFF äquivalente.
Die zwei Boot-SSDs wurden aus Performace gründen hinzugefügt und speichern alle VMs.
Der DL380 ist zudem für einen Server seiner Leistungsklasse recht Stromsparsam, sodass ein Leerlaufverbrauch von unter 100 W gemessen werden kann.

## Software
Folgende Software ist auf dem Server installiert:
- Proxmox
  - TrueNas Scale
    - NextCloud (Als App mit direktem zufriff auf TrueNas Speicher)
  - Debian (Als Docker Host für Betriebskritische Anwendungen)
    - Keycloak (Authentifizierungsservice)
    - VPN Endpunkt
    - Cloudflare Tunnel Endpunkt
    - PI Hole 
  - Debian (Als Docker Host für Betriebsunkritische Anwendungen)
    - Zentraler Passwortmanager 
  - Debian (Als Docker Host für Anwendungen der Live Übertragung auf YouTube)
    - Bitfocus Companion
    - XIBO CMS
    - Tally Arbiter
    - Restream
  - Debian mit installiertem TBMQ MQTT Broker

 Jede Softwarekomponente ist in unserem Anwendungsfall kostenlos nutzbar.
 Bei eigener Umsetzung sollte zwingend auf die Lizenzvereinbarungen der Softwarehersteller geachtet werden.

 

