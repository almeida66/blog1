---
tags: libreboot
---
Keine Lust auf Hersteller-Schweinereien im BIOS? Dann wird es Zeit für [libreboot](https://libreboot.org/); wie der Name schon sagt: frei - und zwar frei von Hintertüren, Sicherheitslücken usw.

Libreboot ist irgendwie parallel zu coreboot entstanden, wobei coreboot je nach sog. Payload wohl auch windows unterstützen kann. Das ist bei libreboot nicht der Fall, hier fehlt sämtliche proprietäre Software.

Wie so oft wird freie Software von Freiwilligen entwickelt und die Zahl der unterstützten Systeme ist sehr übersichtlich; aber ThinkPads sind dabei :)

Also habe ich einen [ThinkPadX60](https://thinkwiki.de/X60) gewählt, dessen Firmware sogar mit der Software-Methode, also aus der Linux-Kommandozeile heraus, ersetzbar ist. Dieses Modell besitzt auch die wenigsten Inkompatibilitäten, wie z.B. die Wlan-Karte von Intel. Man sollte noch die aktuellste proprietäre BIOS- und EC-Version (embedded controller) installieren.

Hier wurde für die verschiedenen Modelle bereits fertige ROMs samt Payloads compiliert. Wer es selbermachen will, dem sei [Trisquel 7](https://trisquel.info/de) als 64-bit dringend empfohlen; damit laufen alle Skripte störungsfrei.

Eigentlich kann man gleich die vesafb mit dem ent. Tastatur-Layout auswählen. Damit hat man später beim Installieren von Betriebssysteme mit GUI weniger Probleme.

Zur Installation verweise ich auf die Original-Seite, ggf. existieren hier und dort vereinfachte Howtos einiger Nutzer. Und sollte doch was schiefgehen, man kann den Chip wieder rückbeschreiben. Da gibt es den spottbilligen CH341A USB-Programmierer. Aber - vorher immer ein Backup mittels `./flashrom/i686/flashrom_lenovobios_sst -p internal -r factory_rom.bin` durchführen. Der Chip kann statt sst auch von macronix sein...

Danach `./flash i945lenovo_firstflash yourrom.rom`, je nach Fehlermeldungen, sowie **BUC.TS=1** den Neustart wagen und anschliessend `./flash i945lenovo_secondflash yourrom.rom`. **BUC.TS=0** und die Meldung Verifying flash... **VERIFIED** sollte erscheinen.

Und nun hat man einen freien und blitzschnellen Systemstart; ich empfehle die künftige Software vorab auf einer anderen Platte zu installieren. Die neue freie BIOS-Firmware ist extrem schnell, dass sogar aktuelle USB-Sticks aufgrund ihrer Lahmheit mehrfach Fehlermeldungen bringen, bevor die Installationsroutine überhaupt greift.
