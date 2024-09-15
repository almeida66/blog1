---
tags: OpenWrt
---
Mal ein Zwischenbericht zur Hardware - die ist eigentlich zu schwach für die Anwendung; daher die "alte" Software wview. Leider waren tägliche reboots notwendig, um den MiniServer halbwegs aktiv zu halten. Dann wurden die hmtl-Seiten nicht mehr neu aufgebaut, usw. usw.

Letztens fiel ich über den [Pogoplug](https://wikidevi.com/wiki/Cloud_Engines_Pogoplug_E02); einige davon haben eine recht ordentliche CPU mit 1,2GHz und einiges an NAND-Speicher.

Für billigst einen gekriegt - schliesslich ist der Anbieter offline und die Teile damit nur blinkendes Plastik - und wären da nicht die findigen Communities... die haben mal wieder Wege gezeigt diesen Plastikschrott zu verwerten. Nämlich mit Linux-Derivaten für ARM-Prozessoren.

Auch [OpenWRT](https://openwrt.org/) kann man dazu zählen; die haben sich eh auf Router u.ä. spezialisiert. So fiel auch hier erste Wahl auf die neueren LEDE-Versionen.

Vorab allerdings der Hinweis, dass sich die Pogoplugs im Originalzustand nur durch den direkten Eingriff über die intern vorhandene serielle Schnittstelle mittels USB/COM-Adapter (PL2303) zum Leben erwecken lassen. Zugriff über putty o.ä. Tools; dann kann man mit **setenv** einige Parameter anpassen und z.B. über den **tftp** ein neues "freies" [U-Boot](https://forum.doozan.com/read.php?3,12381) aufspielen.

Damit kann man dann von USB-Stick starten und eine ordentliche Software verwenden. OpenWRT hat den Vorteil klein zu sein und vollständig im NAND Platz zu finden. Danach folgen die üblichen Schritte zu Vervollständigung der Software (hier python) für die Anwendung einer aktuelleren Übertragungssoftware [weewx](http://www.weewx.com/) .

Damit ist die Wetterstation WRX815 (alias TE923, Hideki, ...) wieder online. Die templates sehen auch viel [schöner](http://weather-server.uk.to:8080/) aus... :)
