---
tags: OpenWrt
---
Eigentlich recht einfach, wenn man den Dreh raushat und endlich versteht. Bin halt kein Netzwerk-Pro... meistens ist die Dokumentation sowas von kompliziert geschrieben, um ja auch den Pros was zu bieten.

Nachdem man einmal den Router seiner/ihrer Wahl - möglichst mit >8Mb - gewählt und idealerweise mehrere davon hat, spielt man die aktuelle [OpenWrt](https://downloads.openwrt.org/releases/)-Firmware drauf (ueblicherweise die **factory**).

Da auch die Mesh-Pakete ständig verbessert werden, macht es Sinn wirklich die neuste Firmware zu laden, aktuell irgendwo bei 19.07. Nach der Umwandlung des Routers mit/in OpenWrt, kann man jederzeit mittels `sysupgrade` zwischen den Versionen springen und testen.

Wir unterscheiden zw. den **Mesh-Access-Point** und einem **Mesh-Point**. Ersteres wird wie ein einfacher Router mit WAN und LAN vorab konfiguriert; d.h. mit WAN-Anbindung ans DSL-Modem (heute häufig eine FritzBox). Somit hat man gleich eine Hardware-Netzwerk-Trennung von der Aussenwelt. Beim Zweitem entfallen die Vorarbeiten an der WAN-Schnittstelle.

Vorbereitungen:
1. **putty** installieren - damit wird über ssh mit dem Router kommuniziert. Leider sind nicht alle Einstellungen über LuCi machbar.
2. Für Zugriff mit dem WWW sorgen, sei es übers Wlan, oder Lan; denn wir müssen einige Pakete laden.
3. Damit der Aufruf mit putty klappt, wird meistens die Vergabe eines Passwortes im Router verlangt. IP lautet bei Erstaufruf: **192.168.1.1**

Aktualisierung der Pakete mittels opkg update; danach folgt die Umwandlung:

`opkg remove wpad-mini wpad-basic` und

`opkg install wpad-mesh`, optional *nano* - ein einfacherer Editor als vi.

`reboot` - ist immer gut.
