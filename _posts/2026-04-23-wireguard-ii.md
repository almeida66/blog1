---
tags: ARM
---
## wireguard ii
Aktuell werden EOL unifi Geräte wie der **USG-3P**, alias UniFi Security Gateway, für wenig € verschenkt und das mit 3x 1Gb Ports. ARM und [OpenWRT](https://openwrt.org/toh/ubiquiti/unifi_security_gateway_3p) tauglich. Da dürfte auch [Wireguard](https://openwrt.org/docs/guide-user/services/vpn/wireguard/server) funktionieren. 

Dazu muss das Gehäuse geöffnet werden und sowohl die USB-Speicherkarte, als auch der Anschluss für die Erstinstallation vorbereitet werden.

Die USB-Speicherkarte wird mittels fdisk vorbereitet und als erste Partition eine 142Mb grosse FAT32 empfohlen, um den Kernel unterzubringen. Der Rest als zweite Partition als ext3.

tbc
