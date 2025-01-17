---
tags: macintosh
---
## MacBook Air Core-i5
Eigentlich hatte ich schon einen in der Sammlung, aber nur 2GB RAM, das reicht ja für fast gar nichts. In der Familie gabs nen Update auf M3 und sie haben mir den "alten" 11" geschenkt. Ein [A1465](https://everymac.com/systems/apple/macbook-air/specs/macbook-air-core-i5-1.4-11-early-2014-specs.html) mit satten 8GB RAM von 2014. 

Dem anderen MacBook Air habe ich den neuen Ersatz-Akku ausgebaut und hier eingesetzt; samt neuerer NVMe-SSD und Adapter. Damit konnte quasi die doppelte Zugriffsgeschw. gemessen werden. Die original eingebaute SSD war/ist von Toshiba mit etwa 695MB/s ([lt. Blackmagic Disk Speed](https://apps.apple.com/de/app/blackmagic-disk-speed-test/id425264550?mt=12)).
An anderer Stelle habe ich bereits beim MacBook Pro mittels [OCLP](https://dortania.github.io/OpenCore-Legacy-Patcher/) **Ventura** erfolgreich installiert, hier kann sogar **Sonoma** recht flüssig zum Laufen gebracht werden.

Idealerweise wird dazu ein installiertes MacOS als Basis genommen und mit einer vorzugsweise schnellen externe NVMe ein Installationsmedium aufgesetzt. Ja, es würde auch direkt auf dem MacBook Air gehen, aber eine Neuinstallation ist immer sauberer und benötigt damit nur die Hälfte der Zeit. Denn die CPU Core-i5 ist weiterhin nicht die flotteste.

Egal, mit OCLP in der aktuellen Version 2.x ist die Installation recht übersichtlich. Mit der sog. *Post-Installation* wird sogar "angeboten" die USB-Startsequenz auf die SSD zu kopieren/installieren. Danach unbedingt die "automatischen Updates" ausschalten - keine gute Idee diese zu starten - denn OCLP bereitet extra für die Nutzung neuerer MacOS Versionen für **alte Hardware** die Treiber vor, die ein *Standard-Update* vermutlich (zu 99,9%) überschreiben wird. 
