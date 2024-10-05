---
tags: macintosh
---
Eigentlich iOS, aber egal, passt in die mac-Familie hinein. Guenstigst erhalten, aber leider bereits verbastelt - hatte mich schon gewundert warum die Scheibe trotz isopropanol nicht sauber wurde...

iPads (hier die 3te Generation mit Wifi+GSM) werden gerne beim Verkauf vergessen zu "entsperren"; d.h. man kommt erst gar nicht in die Programmebene, sondern bleibt in der Anmelderoutine haengen. Ja, es existieren Hacks, darunter auch die Option mittels Entfernung einiger Widerstaende R1204 (R1205). Wie bei meinem Exemplar geschehen, nur leider stuemperhaft.

Ich habs dann mittels Software-Hack [checkm8-a5](https://github.com/synackuk/checkm8-a5) versucht die Startprozedur beim A5x Chip zu veraendern; hierbei wird der Code mittels Arduino IDE idealerweise auf ein **Arduino uno** geladen und mit einem *USB-Host-Adapter* ans iPad im DFU-Modus angeschlossen. Dann mit dem [ipad3Bypasser](https://alwaysappleftd.com/downloads.html) die RAMdisk gelöscht bzw. das Setup veraendert. Ggf. auch Sliver zu verwenden. Soweit die Theorie, klappt aber nicht mehr - apple hat wohl die Luecke gestopft. Hilft nur ein Ersatzboard aus China...

> [!NOTE]:
> es funktioniert doch, aber ueber Umwege mittels python-Skripte [iPro beta](https://alwaysappleftd.com/ipro_beta_program.html) und unter Zuhilfenahme von Sliver um den SSH-port zu oeffnen und die Setup.app zu entfernen. Die Verzeichnis-Pfade in den sh-Dateien des iPro sind vermutlich noch anzupassen - immernoch *beta*. Das Ganze via Mac.

Leider klappt(e) das *Aktivieren* immernoch nicht, damit wurde es schwierig alte Apps nachzuladen... dafuer ist nun das Ersatzboard aus China angekommen. Und mit [sideloadly](8https://sideloadly.io/) klappt es nun alte Apps zu verwenden.
