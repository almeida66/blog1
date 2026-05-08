---
tags: ARM
---
## wireguard ii
Aktuell werden EOL unifi Geräte wie der **USG-3P**, alias UniFi Security Gateway, für wenig € verschenkt und das mit 3x 1Gb Ports. ARM und [OpenWRT](https://openwrt.org/toh/ubiquiti/unifi_security_gateway_3p) tauglich. Da dürfte auch [Wireguard](https://openwrt.org/docs/guide-user/services/vpn/wireguard/server) funktionieren. 

Dazu muss das Gehäuse geöffnet werden und sowohl die USB-Speicherkarte, als auch der Anschluss* für die Erstinstallation vorbereitet werden.

Die USB-Speicherkarte wird mittels fdisk vorbereitet und als erste Partition eine 142Mb grosse FAT32 empfohlen, um den Kernel unterzubringen. Der Rest als zweite Partition als ext3.
Das anschliessende Kopieren des neuen Kernels erfolgt mit `cp sysupgrade-ubnt,usg/kernel kernel/vmlinux.64`, samt zug. md5. Der Kernel ist Bestandteil der sysupgrade-Datei.  

Der Rest wird via **dd** auf die zweite Partition aufgespielt; mittlerweile ist auch die LuCi-Oberfläche eingefügt, somit kann diese direkt über LAN1 unter 192.168.1.1 erreicht werden. LAN2 ist bei der Erstinstallation nicht konfiguriert. *Den Zugang über RS232 auf den Consolenport kann man sich sparen.

Auf das USG-3P wurden kurzerhand die Dienste der entfritzten FB verschoben plus wireguard aufgesetzt.

Durch die schiere Menge an Ethernet-Ports werden 1xWAN, 1xLAN2 für den Admin-Zugang und 1xLAN1 für den Notzugang (br-lan, nicht gesteckt) verwendet. Durch den aktiven 2ten Ethernet Port muss im Router (hier FB) eine statische Route auf die IP der VPN mit GW zur LAN2 gesetzt sein. Bei der Firewall sind LAN und LAN2 separat zu steuern. Portfreigabe 51820 is klar...
