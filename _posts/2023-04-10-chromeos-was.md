---
tags: libreboot
---
## ChromeOS, was?
Spielerei, aber die Chromebooks sind im Gegensatz zu den lahmen Netbooks a lá *eee* und Co schon recht flott. Waere da nicht dieses unsaegliche ChromeOS - wenn man es mag... ist mir zu handyartig... und neugierig.

Hab nen Toshiba [CB30-B-104](https://www.notebookcheck.com/Test-Toshiba-Chromebook-2-CB30-B-104.147309.0.html) ergattert, alias Swanky, Bay Trail mit 2 cores als 13". Kleines Schoenheitsfehler - die aufgeloetete eMMC mit 16GB; kann man mit USB3-SSD-Adapter oder SD-Karte umgehen - Platz waere im Innern des Gehaeuses vorhanden.

Als Erstes wird erstmal das BIOS plattgemacht und zwar mit denen von [MrChromebox](https://mrchromebox.tech/). Er benutzt SeaBIOS, um die Chromebooks zu "befreien", d.h. man kann dann andere Linuxe und stellenweise FreeBSD aufspielen. Windows ggf. bedingt - habs nicht ausprobiert (bei 16GB).

Meistens muss man die hardware seitige BIOS-Schreibsperre im Innern entfernen (Schraube, Schalter oder metall. Aufkleber), das Chromebook in Developer Modus umstellen und eine *Shell* starten. ChromeOS ist im Endeffekt auch ein linuxoides OS...

Dann wird ein Skript von obiger Seite geladen und ausgefuehrt; man kann zwischen teil- und vollstaendiger Ersatz des BIOS waehlen. Ich habe das 2te ausgewaehlt, geflasht und ein "black screen" erhalten - na toll.

Da ich ein CH341a programmer rumliegen hatte - wollte ich schon immer mal einsetzen - musste ich noch ein 1,8V Adapter besorgen und den SOIC8 Baustein mehrfach geflasht. Irgendwann hat es funktioniert. Es liegt u.a. am Toshiba CB30-B; das SeaBIOS funktioniert.

So, nun kann man von DietPi, Xubuntu, Trisquel/Debian bis FreeBSD (tested) alles aufspielen - aber moeglichst sparsam, da nur 16GB vorhanden sind. Meistens muss man **iwlwifi 7260** und **firmware-sof-max98080** für die internen Lautsprecher nachladen. Der Bildschirm lautet eDP-1 und kann bei FreeBSD schonmal zicken.

Fuer die (Funktions-)Tastenbelegung existieren [hier](http://www.fascinatingcaptain.com/projects/install-ubuntu-on-the-toshiba-chromebook-2-in-5-steps/) und dort einige Skripte fuer die Nutzung in Linux, allerdings bei *Xorg* nur z.T. zu gebrauchen.

Die Helligkeit (Brightness) kann nicht ohne weiteres via Funktionstasten reduziert werden. Hier hilft entweder ein `xrandr --output eDP-1 --brightness 0.8x` oder halt ein beherztes `echo 4000 | sudo tee /sys/class/backlight/intel_backlight/brightness`. Bei Verwendung von **xbacklight** muss dieses explizit in der *xorg.conf* angegeben werden.
