---
tags: NetBSD
---
Mittlerweile die dritte Eingabe, weil der Raspi wohl die microSD gekillt hat.

Hier der kurze Ueberblick fuer die Installation von netbsd (x86, arm7):
Das gezogene Image wird mittels **dd** auf ein ent. Speichermedium geschrieben.
Es folgt die Passwortvergabe und Installation eines users:
```
useradd -m -G wheel user
passwd user
```
Es folgen an microSD angepasste Eingaben in */etc/rc.conf*:
```
syslogd=NO
manpagedb=NO
savecore=NO
virecover=NO
fsck_flags="-P -p -y"
no_swap=YES
```
Darueberhinaus die Verwendung von **tmpfs** in */etc/fstab*, sowie die Anpassung des Tastaturlayouts in */etc/wscons.conf* *"encoding de"*

Die Umgebungsvariable `PKG_PATH="http://cdn.NetBSD.org/pub/pkgsrc/packages/NetBSD/ARCH/VERSION/All"` wird gesetzt und exportiert.

Es folgt ein erstes `pkg_add pkgin`; danach ein `pkgin update`. Und nun die Installation von:
- lighttpd
- mc
- ddclient (+perl)
- php-xx
- p5-CGI
- p5-HTML

Obige Listeneintraege sind stellenweise untereinander verbunden bzw. werden z.T. automatisch installiert. **Ddclient** dient der Aktualisierung eines vorhand. dynDNS freier Anbieter.

Ggf. die feste Vorgabe der IP-Adresse via 
```
auto_ifconfig=YES
ifconfig_ethx="inet...netmask..."
lighttpd=YES
ddclient=YES
```
