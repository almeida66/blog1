---
tags: hackintosh
---
## hackintosh auf ThinkPad R40
Nachdem im Zuge der OS/2 Warp Installation nun ein [ThinkPad R40](http://thinkwiki.de/R40) die Sammlung ergänzt, wurde gleich das uebliche Prozedere ausprobiert: WinXP, Linux und Mac OS für x86 als Triple-Boot.

Die fehlenden Treiber bietet nun Lenovo an, der Rest ist Probieren...

Idealerweise fängt man mit eine Live-LinuxCD und teilt mittels gparted die HDD ein, z.B. sda1=winxp, sda2=OSx86, sda3=linux usw. Start-Installation wird nun Windows sein, danach sollte man Mac OS installieren. Hierbei wird (hier) mittels `fdisk -e /dev/rdisk0` und flag 2, update, write, quit, reboot die 2te Partition für Mac OS als Bootpartition gesetzt. Mac OS Installation starten, Partition formatieren und die geeigneten Treiber auswählen (ThinkPads sind etwas heikel). Neustart unbedingt mit Flag -f durchführen. Testen!

Jetzt (oder später) von der Installations-DVD den Unterordner i386 auf usb o.ä. kopieren; dieser ist versteckt (Stichwort: hidden) unter /usr/standalone/i386!

Läuft alles? Dann mittels der Install-DVD den Single-User-Mode mittels -s aufrufen und die Bootpartition wieder auf 1 setzen.

Dann mit der Linux-Installation starten und anschliessend grub auswaehlen. Der Unterordner /i386 wird nun unter /boot/grub kopiert und in menu.lst der Zusatzeintrag "title OSx86" mit Angabe von "root (hd0,1)" (hier die 2te Partition) und "chainloader+1" eingeben.

Neustart und freu, freu :) alles da.

REFIt habe ich ausprobiert, aber da passierte nix, ThinkPad, halt. BootCamp soll nur Windows erkennen, also uninteressant.
