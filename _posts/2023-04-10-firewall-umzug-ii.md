---
tags: thinclients
---
## firewall umzug ii
Leider zu frueh gefreut, die Logfiles haben durch eine Miskonfiguration die SD-Karte geschreddert; wundert mich warum dies beim amd64 nicht zu aehnlichen Verhalten gefuehrt hat.

[C't](https://www.heise.de/select/ct/2023/6/2301013201757655367) sei Dank (oder auch nicht) kann mit [proxmox](https://www.proxmox.com/de/) eine wunderpraechtige virtuelle Umgebung fuer diverse Systeme halbwegs ressourcensparend hingezaubert werden.

Ich verwende noch den Futro S900 als firewall, dieser ist zwar lahm(er), hat aber einen Anschluss fuer eine ausgewachsene Ethernet-Karte. Was die anderen mini Futros nicht haben, wie der vorgestellte S740. Durch den c't-hype findet man die Teile nun nicht mehr - alles aus 2te Hand weggekauft.

Aber der Futro S720 funktioniert auch gut, hat zwar nur 2 Cores - mein Exemplar mit 2x1.65GHz, kann aber mit 8GB RAM bestueckt werden. Und hat einen 2ten mPCIe Anschluss fuer die 2te notwendige[^note] Ethernet-Karte. Eine grosse mSATA SSD rundet das Ganze ab.

Dadurch bin/war ich in der Lage diverse mini-Server zusammen zu packen.

Ausser der eigentlichen Installation des akt. proxmox (debian!) koennen fuer sog. Container und/oder virtuelle Maschinen folgende [Hilfsskripte](https://tteck.github.io/Proxmox/) verwendet werden; die VMs werden mit Hilfe der Installationsdateien (ISO) aufgebaut.

Als *Container* laufen: **AdGuard, Gopher, MQTT und node-red**

Als *VM*: **pfsense und ein NetBSD-webserver**

Testbetrieb folgte... und es funktioniert trotz nur 8GB RAM. Eine Backup-HDD kam via SATA hinzu und dient fuer die eingebaute Backup-Funktion als externe Plattform.

[^note]: Man kann einen 2ten LAN-Anschluss via VLANs simulieren, aber fuer eine firewall sollte schon eine echte LAN-Karte verwendet werden; schon aus Gründen einer möglichen Misskonfiguration - je nach Umfang der Topologie

![](http://almeida66.github.io/blog/img/interface1.png)
(c) c-nergy.be
