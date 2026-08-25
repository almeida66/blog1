---
tags: OpenWrt
---
Um mit [allsky](https://github.com/AllskyTeam/allsky) was sinnvolles anzufangen, ist es fast ein Muss die Bilder auch öffentlich via webserver bereitzustellen. 
Für dieses Unterfangen habe ich hier noch einige unifi gemoddete [USG](https://openwrt.org/toh/ubiquiti/unifi_security_gateway_3p) rumliegen, die aufgrund des USB-Sticks einiges an Daten + Schreibzyklen  zulassen und mehrere Ethernet-Ports aufweisen um hardware-technisch lan-wan strikt zu trennen.
Da nach einem Defekt ich da wieder blank stand - ohne die genauen Schritte aufgeschrieben zu haben - was das etwas doof...

Nach obiger Neuinstallation wird das OpenWrt auf das neueste hochgezogen, aktuell sowas wie 25.12.xx. Es folgt die Auflistung:
- mc, nano, irqbalance (fürs handling)
- [lighttpd](https://openwrt.org/docs/guide-user/services/webserver/lighttpd) und notwendige module (cgi, simple_vhost)
- ddns-skripte, curl , **bind-host** und ent. luci-mod
- sftp-server (openssh)
- [shadow-user](https://openwrt.org/docs/guide-user/additional-software/create-new-users)-Skripte, ggf. noch shadow-groupadd
- [php](https://openwrt.org/docs/guide-user/services/webserver/php) und php-cgi (aktuell in der 8er Version)

Allsky sendet via sftp die Bilddateien auf den webserver; je nach lighttpd-Installation heisst der benutzer=**http** oder www-data. Genau für diesen wird ein home-Verzeichnis /home/http/allsky mittels `mkdir -p /home/benutzer/` erzeugt. Ja, man kann es anders benennen, so spart man sich halt Nacharbeiten. Danach ein `useradd -m -d /home/benutzer -s /bin/ash benutzer`, `passwd benutzer` und schliesslich `chown -R benutzer:benutzer /home/benutzer`. 

Bei der Erstinstallation von lighttpd geht OpenWrt davon aus, dass man den uhttpd ersetzen will und sperrt den web-Zugang, d.h. man sollte also übers ssh-terminal weitermachen und via `/etc/init.d/lighttpd stop` killen und weitermachen. Z.B. mit der Ergänzung von */etc/config/dhcp* 
```
config domain
      option name 'luci'
      option ip '192.168.1.1'

config domain
      option name 'allsky'
      option ip '192.168.xx.xx'
```
In der Firewall: 
```
config redirect
        option src              wan
        option src_dport        8081
        option dest             lan
        option dest_ip          192.168.xx.xx
        option dest_port        8081
        option proto            tcp

config rule
        option src              wan
        option dest_port        8081
        option target           ACCEPT
        option proto            tcp
```
Und im lighttpd-Modul simple_vhost:
```
$HTTP["host"] =~ "^allsky(\:[0-9]*)?$" {
    dir-listing.activate = "disable"
    server.document-root = "/www1/"
    $HTTP["url"] =~ "^/cgi-bin" {
        cgi.assign += ( "" => "" )
    }
}
```
Bei den anderen Modulen sind ggf. die Pfade für php bzw. cgi zu aktualisieren, gilt auch für die lighttpd.conf; dort noch server.port = 8081 eintragen (je nach Bedarf).

Je nach Umgebung muss dann im vorgelagerten Modem+Router (z.B. FB) die Portfreigabe für http-Dienst 8081 angegeben werden. Der Rest ist via dynDNS und je nach Anbieter anzugeben.
