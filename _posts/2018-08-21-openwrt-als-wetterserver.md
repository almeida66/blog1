---
tags: OpenWrt
---
Ich habs wieder getan: da meine Webcam mangels Durchlass (firewall) keine Fotos auf die homepage senden konnte, habe ich den TL-MR3020 für ein anderes Projekt anvisiert.

Eine Wetterstation; nein, ich werde kein Wetterfrosch, es geht alleine um die Linuxseite des Projektes... Das Teil - eine **WRX815**, alias Nexus, Hideki usw. usw. habe ich günstigst für 30€ gekriegt - nun ja, es fehlte der UV-Sensor und der Windmesser, dafür waren 2 extra Temperaturfühler samt Regensensor vorhanden.

Ziel: eine webbasierende Anzeige, damit man jederzeit das Wetter vor der eigenen Tür weiss.

Die kleinen Router haben ja ein Speicherplatzproblem, gerade mal 4MB. Auch die aktuellste OpenWRT Firmware (lede) ist zu gross. D.h. man muss unnötige Programme löschen, am besten über die Konsole, da die LuCi-Umgebung nicht ganz sauber anzeigt.

Für obigen Router ist die Version 14.07 am ehesten geeignet, wir benötigen etwa 470kb freien Speicherplatz für den usb-storage und ext4 Support. Am besten mit ipv6 und zug. Softwareabh. anfangen.

Danach dieses mittel `opkg install kmod-usb-storage block-mount kmod-fs-ext4 kmod-scsi-core` laden.
Wenn das geklappt hat, einen formatierten USB-Stick einstecken und mounten. Das Systemverzeichnis mittels `tar -C /overlay -cvf - . | tar -C /mnt/usb -xvf` - auf den Stick übertragen und nun unter /etc/config/fstab die Verzeichnisse anpassen:
```
config 'mount'
option target /overlay
option device /dev/sdx1
option fstype ext4
option options rw,sync
option enabled 1
option enabled_fsck 0
```
Und erst jetzt ein reboot. Wenn man kein Fehler gemacht hat, stehen nun unendlich viele Gbytes zur Verfügung...

Ich verwende das kostenlose [wview](https://sourceforge.net/projects/wview/) für die Datenübertragung von der Wetterstation
auf das WWW. Den Rest finden man im Wiki auf [OpenWrt](https://wiki.openwrt.org/).

Das Ergebnis hier zu sehen.
