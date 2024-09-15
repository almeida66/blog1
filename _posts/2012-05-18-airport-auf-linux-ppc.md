---
tags: macintosh
---
## airport auf linux PPC
Nach den ersten Installationshürden will man auch eine aktive WLAN-Verbindung am iMac G3 nutzen.

Je nach Airport-Karte (hier die "normale" mit Lucent orinoco) wird unter Linux PPC nur bis WPA-TKIP unterstützt.
Was man benötigt: firmware-linux-nonfree (agere_sta_fw.bin) und die wireless-tools, sowie wpa_supplicant.
Mit iwconfig, ifup und ifdown hat man alle Befehle parat. Idealerweise wird in interfaces die passende Schnittstelle (eth1 oder wlan0) eingetragen. Wichtig ist weiter der Eintrag in der wpa_supplicant.conf (bei Verwendung von WPA): ap_scan=2

Möglich dass es Distri abhängig ist, aber mit wicd habe ich die Airport-Karte nicht zum Laufen gebracht; eben weil ap_scan=2 fehlt...
Der Rest ist aus den Manuals/howtos zu entnehmen.
