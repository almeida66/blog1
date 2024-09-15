---
tags: ARM
---
Ich verwende gerade einen riesen Kasten als amd64 [pfsense](https://www.pfsense.org/)-Firewall, die irgednwo bei FreeBSD 12.3 stehengeblieben ist. Nicht weiter schlimm, aber der Kasten muss weg.

Mittlerweile tummeln sich ARM-Platinchen mit 2 Ethernet-Buchsen und viel CPU-Power samt zug. RAM, wie raspi, orangepi, nanopi usw. usw. auf dem Markt.

Pfsense bietet die auch an, fuer netgate-Minis, die kosten aber und zwar richtig viel - fuer wenig. Auch [ipfire](https://www.ipfire.org/) ist eine Alternative, aber dieses proxy-Zeugs passt nicht in meinen Netzwerk-Aufbau.

Also kommt [opnsense](https://opnsense.org/), quasi ein freier fork, fuer ARM in Frage. Eigentlich nicht offiziell, aber das haben die aus der Community super umgesetzt.

Ich bin dann ueber ein [orange pi r1 plus](http://www.orangepi.org/html/hardWare/computerAndMicrocontrollers/details/orange-pi-R1-Plus.html) gestolpert. Mit satten 1.5GHz und 1GB RAM und 2x Ethernet-Buchsen. Und das alles auf etwa 58x58mm.

Fuer den rk3228-Chip muss man allerdings das ueblich verteilte rockchip64-Image manipulieren mit dem passendem [u-boot](https://mirrors.dotsrc.org/armbian-apt/pool/main/l/linux-u-boot-orangepi-r1plus-current/) versehen. Die Dateien holt man sich aus der deb heraus und spielt sie via dd ein:
```
dd if=idbloader.bin of=/dev/sdb seek=64 conv=notrunc
dd if=uboot.img of=/dev/sdb seek=16384 conv=notrunc
dd if=trust.bin of=/dev/sdb seek=24576 conv=notrunc
```
Eine freeBSD-Installation ist hilfreich, um auch die *dtbs* und *overlays* des orangepi r1+ anzupassen. Und ein Hinweis noch: *putty* verbindet sich hier mit satten **1500000**.

Es folgt die Verwendung der opnsense-github-tools, um opnsense fuer ARM aufzusetzen, oder man holt sich das Image der vielen Community-Programmierer.

Die des nanopi r2 sollte zu 99% identisch sein - sieht aus wie OEM des orangepi aus, namens Xulong - keine Ahnung wer tatsaechlich der Hersteller ist. 
