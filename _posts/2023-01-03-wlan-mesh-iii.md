---
tags: OpenWrt
---
## OpenWrt und mesh iii
Quasi die Fortfuehrung; aufgefallen bei der Aktualisierung der Systeme auf 22.03. Mittlerweile ist die Anleitung unter [openwrt](https://openwrt.org/docs/guide-user/network/wifi/mesh/80211s) auch verstaendlicher geworden.

Nach dem Upgrade und dem Update der Pakete via opkg, schmeisst man **wpad-basic-wolfssl** raus. Vermutlich vom Geraetetyp und/oder Installation abhaengig; ich verwende nur Router vom Chiptyp Atheros, die funktionieren am problemlosesten. **Wpad-mesh-openssl** ist uebrigens meist zu gross (1,7MB).

Danach `opkg install wpad-mesh-wolfssl` und **mesh11sd** (schadet nicht), sowie **nano**. Dann folgt unter */etc/config/wireless* der wichtige Teil:
```
config wifi-iface 'mesh'
option network 'mesh'
option device 'radio0'
option disabled '0'
option mode 'mesh'
option ifname 'mesh0'
option network 'lan' # das ist die bridge!
option mesh_id 'my-mesh-id'
option encryption 'sae'
option key 'geheim'
```
Radio0 steht fuer den 2.4GHz Teil, sonst radio1 - gemaess einem Beitrag im [linux-magazin](https://www.linux-magazin.de/ausgaben/2022/02/wlan-mesh-teil-1/) eine gute Idee das mesh-Netz auf 5GHz zu teilen und die Access-Points mit 2.4GHz fuer die "Altgeraete" zu betreiben.

Habs noch nicht probiert, da eine der Stationen trotz drei Antennen kein 5GHz anbietet und schon gar kein "Triband".

Das Ausfuehren von wifi startet den Part neu oder halt ein reboot. Test mit `iw dev mesh0 info`, oder ein `iw dev mesh0 station dump`.

Jeweils den Access-Point pro Router einrichten, Stichwort MAP und MPP.

Moeglich dass nun in 22.03. die Pakete ausgereifter sind, oder es liegt am verwendeten wolfssl - es funktioniert auf Anhieb tadellos.
