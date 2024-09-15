---
tags: macintosh
---
## linux PPC auf iMac G3
Nun ja, es musste ja so kommen. Was macht man mit dem ganzen freien HDD-Platz neben Mac OS X? Da war doch was mit Linux PPC...
Also schnell die üblichen Quellen angezapft und schnell wurde klar, dass debian ppc die beste Lösung sei.

Tja, wäre da nicht das eigenwillige iMac CD-Laufwerk. das nimmt nicht jede CD und booten schon gar nicht. Hilfreich ist ein externes USB-CD-Laufwerk. Und weiter?
Dieser iMac gehört bereits zu den NewWorld mit der sog. OpenFirmware. Die Tastenkombination cmd-opt-o-f bringt uns weiter, nämlich in die OpenFirmware. Dort kann man den USB-Port ansprechen und zum booten bewegen.

Mit <`dev / ls`> findet man schnell die USB-Schnittstelle, die etwas kryptisch daherkommt.
In etwa mit <`boot usb1/disk@1:2,\\yaboot`> sollte es klappen. Man erhält dann die Auswahl (je nach Distri) zwischen standard/GUI und expert. Wegen der Anzeigeproblematik beim G3 ist expert und der Zusatz video=ofonly dringend zu empfehlen. Yaboot ist übrigens der bootloader.
Alles andere ist debian-like easy.

Ich sollte ggf. erwähnen, dass bei einer Parallelinstallation mit Mac OS X die HDD-Partitionierung unter OS X nützlich ist. Eine live-Distro a la´ finnix kann mit mac-fdisk die 800k grosse sog. bootstrap nachträglich einbasteln, aber die Gefahr die Mac OS X Partition unbrauchbar zu machen, ist gross. 
