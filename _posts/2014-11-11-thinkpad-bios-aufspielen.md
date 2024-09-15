---
tags: IBM
---
Ein neues BIOS aufspielen ist ja nichts besonderes, aber nicht wenn der Akku defekt ist und mangels Disketten-Laufwerk das Schreiben der DOS-Dateien schon die erste Huerde darstellt.

IBM ThinkPads sind da sehr eigen und verweigern die Zusammenarbeit. Zum Glueck haben andere Anwender saemtliche Tipps parat.

1. Die BIOS Datei wird als non-diskette heruntergeladen. Diese kann mittels passenden Tools entpackt und das Image extrahiert werden.

2. Fuers USB-Stick wird das HP-Formattool und z.B. das Win98-DOS als Startdisk verwendet. Das bekannte usb-DOS wird nicht funktionieren (siehe spaeter). Die extrahierten Image-Dateien aufs Stick kopieren.

3. a) Fuer defekte Akkus hilft im Normalfall das beigefuegte **flash2** mit der Option /u.
b) Wenn nicht, dann `phlash16 /exit $filename.FL1`. Dieses Tool verweigert die Arbeit, wenn himem.sys (wie beim usb-DOS) aktiv ist!
