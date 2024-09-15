---
tags: OpenWrt
---
## OpenWrt und mesh II
Wir steigen dann in die Kommandozeile und geben ein `nano /etc/config/wireless`

Am Ende der Datei geben wir ein:
```
config wifi-iface 'mesh'
option network 'mesh lan'
option device 'radio0'
option mode 'mesh'
option mesh_id 'housemesh'
option encryption 'sae'
option key 'meshpasswort'
option mesh_fwding '1'
```
Obiges gilt jetzt für ein einfaches 2,4GHz Wlan, bei 5GHz kaeme analog der Eintrag **radio1** dazu. Speichern und das Kommando `wifi` ausführen, ggf. ein `reboot`.

Weiter beim Router 1 als MAP (Mesh-Access-Point); fast alles über die Web-Oberfläche:
- WAN wird als Client mit einer IP des DSL-Routers-Netzes versehen: 192.168.yy.25
- LAN unter **Physical-Settings** den Haken bei *Enable STP* setzen
- DHCP aufsetzen
- WLAN aufsetzen
- LAN mit einer internen IP versehen: 192.168.xx.250
Beim LAN sollte die IP mittels Kommnadozeile `nano /etc/config/network` eingetragen und mit `/etc/init.d/network restart` neu gestartet werden.

Weiter beim Router 2,3,4,.. MP (Mesh-Point); analog zu oben, aber:
-Kein WAN notwendig, wird inaktiv bei der Funktion Switch gesetzt, d.h. VLAN2 gelöscht und bei VLAN1 als untagged markiert. Kann als LAN verwendet werden.
- Kein DHCP, da bereits über Router 1 bedient.
- LAN mit einer internen IP versehen: 192.168.xx.251 oder 252, 253,... (jeweils mit GW und DNS von Router 1)

Fertich. Router 2,3,4 können OHNE LAN-Anschluss rumstehen und dasselbe WLAN zur Verfügung stellen, während im Hintergrund das Mesh-Netz alle miteinander verbindet.

>[!NOTE]
>obige Topologie ist ein Beispiel, in dem es eine gewollte Trennung zw. DSL-Router und internes Netzwerk umgesetzt wird. Man kann natürlich direkt am DSL-Router hängen, d.h. der sog. MAP wird auch als MP aufgesetzt.
