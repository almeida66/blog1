---
tags: ARM
---
Eigentlich ist pi-Hole gemeint, aber es kommen neuere Tools auf dem Markt, z.B. [AdGuard](https://adguard.com/de/adguard-home/overview.html).

Dafür stand als Testobjekt ein Raspi 0 mit Netzwerk-Aufsatz zur Verfuegung. Als Unterbau kommt statt Raspbian Lite, [DietPi](https://dietpi.com/) zum Einsatz. Basiert zwar auch auf Debian, aber schlanker...
Installation des Images auf SD mittels bekannter Tools und es folgt beim ersten Start die Vorinstallation mit update der Pakete. Das dauert etwas beim Raspi 0. Ueblicherweise erfolgt ein Neustart und dann kann man ueber *dietpi-launcher* loslegen.

Hier geht es um einen Werbeblocker, als Ergänzung und/oder Unterstützung der bereits vorhandenen Kombi OpenWrt/Adblock.

Unter DietPi sind sowohl der **pi-hole** als auch **AdGuard Home** als Software verfuegbar. Also warum den Umweg über wget nehmen. Hierbei wird AdGuard automatisch als service konfiguriert. Der Rest erfolgt im eigenen web-interface und zwar als "admin". Der Port kann je nach Installationsmethode variieren.

Im Vergleich zu OpenWrt/Adblock finde ich (bisher) den Raspi 0 stabiler, ja quasi gelangweilt, bei ~3% CPU Belastung.
