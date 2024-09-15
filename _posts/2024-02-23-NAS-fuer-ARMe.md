---
tags: ARM
---
## NAS fuer ARMe
Wie der Titel schon sagt: eine NAS (Network Attached Storage) und wieder mal mit ARM-Technologie. Zwei Schaechte genuegen um die Foto- und Musik-Sammlung auf HDD/SDD zu speichern. Hab wieder was recycelt, schon der Umwelt wegen. Eine Zyxel [NSA325v2](https://openwrt.org/toh/hwdata/zyxel/zyxel_nsa325) und eine QNAP TS-228.
Erstere kann OpenWrt vertragen (kirkwood), analog zum bereits beschriebenen pogoplug, die Zweite vertraegt aktuell nur QNAP-eigene Firmware, dafuer wird diese noch regelmaessig aktualisiert. Keine RAM-Monster, aber mit 1Gb geht schon was. Die LAN-Landschaft ist eh etwas inhomogen und stellenweise "nur" bis 100Mbit ausgelegt.

Egal, Thema ist die Installation mit OpenWrt. Leider sehr trikky, das neue uboot muss idealerweise mit einem FAT32 formatiertem USB-Stick geladen werden, welches natuerlich nicht erkannt wurde. Tatsaechlich duerfte die Win10-Formatierung Schuld sein, da auch eine SSD nicht funktioniert hat.
Ach ja, eine serielle Anbindung muss gegeben sein, via USB-to-Serial-Adapter, also vorher das Gehaeuse wegbasteln.
Mit linux hat die **FAT32** formatierte SSD dann geklappt und statt `usb reset`, wird ein `ide reset` sowie `ide load` notwendig.
```
usb reset
fatload usb 0 0x1000000 u-boot.kwb
nand erase 0x0 0x100000
nand write 0x1000000 0x00000 0x100000
reset
```
Die notwendigen Dateien sind im jew. Release unter *kirkwood* vorhanden. Und das wichtigste dann:
```
setenv mtdparts 'mtdparts=orion_nand:0x00c0000(uboot),0x80000(uboot_env),0x7ec0000(ubi)'
setenv bootcmd 'run setenv bootargs; ubi part ubi; ubi read 0x800000 kernel; bootm 0x800000'
saveenv
reset
```
Die MAC-Adresse VORHER aufschreiben und jetzt abspeichern:
```
setenv ethaddr AB:CD:EF:00:00:00
saveenv
```
Zu guter letzt die eigentliche Software:
```
usb reset
fatload usb 0 0x2000000 firmware.bin
nand erase.part ubi
nand write 0x2000000 ubi 0x600000
```
Ein abschliessendes `reset` tut gut. Dann sollte ein frisches OpenWrt starten, das anschliessende Update geht ueber die OpenWrt-Oberflaeche. Ich sollte beim Code  vielleicht ein (c)OpenWrt setzen, ist schliesslich deren Vorarbeit.
