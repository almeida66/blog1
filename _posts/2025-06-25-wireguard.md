---
tags: ARM
---
Wireguard gilt als das aktuelle nonplusultra *sparsame* **VPN-Softwaretool** und läuft sogar auf Kleinst-Computer à lá ARM, hier in Form eines [orangePi R1+](http://www.orangepi.org/html/hardWare/computerAndMicrocontrollers/details/orange-pi-R1-Plus.html) mit satten 1GB RAM und einem RK3228 mit 2x Gigabit Netzwerk-Ports.

Ein Luxus fürs OpenWrt; und quasi eine Empfehlung aus der [ct](https://www.heise.de/select/ct/2023/6/2301115265162158478), da der orangePi R1+ nahezu mit dem nanoPi R2S identisch ist. Fraglich wer vom wem was kopiert hat. Egal, Leistung ohne Ende für das geplante Vorhaben.

Auch hier eine Idee aus der ct, allerdings unter OpenWRT. Also [image](https://openwrt.org/toh/hwdata/xunlong/xunlong_orange_pi_r1_plus) draufspielen und mit `opkg update` die Daten aktualisieren; neuere images verwenden wohl schon das neue `apk update` und dann benötigen wir ja aufgrund der sich taeglich veränderden IP-Adresse ein dynamisches DNS, alias dynDNS. Dafuer stellt OpenWRT die Sammlung `opkg install luci-app-ddns` bereit. *Reboot* tut gut.

Am besten einen freien dynDNS-Anbieter in Europa aussuchen, da existieren einige... Haengt halt von der gedachten (hobby-)Anwendung ab, wieviel Geld und Sicherheit man investieren will. Dann kommt wireguard mittels Aufruf `opkg install wireguard-tools luci-proto-wireguard` an die Reihe, ggf. mit dem einen oder anderen Zusatzhilfspaket. *Reboot* nicht vergessen.

Einige Vorarbeiten sollte man z.B. an der FritzBox (o.ä. Modem) durchgeführt haben, naemlich die Portfreigabe für **UDP 51820**, jeweils ipv4 und ipv6!

Grob wird man folgende Tätigkeiten ausführen (siehe die vielen Hilfen aus dem Internet oder [hier](https://openwrt.org/docs/guide-user/services/vpn/wireguard/server)):
+ create interface vpn
+ create firewall (accept)
+ create static route (optional)
+ create peer + keys
Letzteres stellt für die Clients (u.a. smartphone) einen QR-Code für die wirklich sehr einfache Übertragung aufs handy.

Damit sollte dann beim handy via browser+vpn "nach Hause" Kontakt aufnehmen können. Ggf. aufs dynDNS achten, die Skripte sind je nach Anbieter schon mal zickig.
