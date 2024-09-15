---
tags: NetBSD
---
Ja, es war nervig. [FreeBSD](http://www.freebsd.org/) hat die Karte erkannt, war aber lahm, [OpenBSD](http://www.openbsd.org/) nicht, also blieb das bekannte [NetBSD](http://www.netbsd.org/) für den kleinen Samsung NC10.

Standard-Installation mit mate als X-Window; das kleine Netbook wurde mit einer SSD + 2GB RAM gepimpt, mehr geht eh nicht.

Und nun das Problemchen: die eingebaute wlan-Atheros-Karte AR5212 ist noch nicht wirklich zu 100% Treiberunterstützt, daher auch nicht unter OpenBSD zur Mitarbeit zu bewegen. Vor allem WPA2-AES mag es nicht.

Egal, mein Problem war wohl die Start-Reihenfolge der Services, daher hier (für mich - is ja auch mein Blog) die Konfig-Lesehilfe:

ifconfig.athx
```
up
ssid "deine AP"
dhcp
```

rc.conf
```
dhcpcd=YES
dhcpcd_flags="athx"
# erst dann den Kram für wpa_supplicant
wpa_supplicant=YES
wpa_supplicant_flags="-i athx -c /etc/wpa_supplicant.conf"
```
wpa_supplicant.conf
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=wheel
network={
ssid="deine AP"
scan_ssid=1
psk="geheim"
key_mgmt="WPA-PSK"
}
```
Weiterhin kann man einige Zusatzangaben eintragen, aber obiges ist das lauffähige Minimum.
