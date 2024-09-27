---
tags: macintosh
---
Eigentlich iOS, aber egal, passt in die Familie hinein. Guenstigst erhalten, aber leider bereits verbastelt - hatte mich schon gewundert warum die Scheibe trotz isopropanol nicht sauber wurde...

iPads (hier die 3te Generation mit Wifi+GSM) werden gerne beim Verkauf vergessen zu "entsperren"; d.h. man kommt erst gar nicht in die Programmebene, sondern bleibt in der Anmelderoutine haengen. Ja, es existieren Hacks, darunter auch die Option mittels Entfernung einiger Widerstaende. Wie bei meinem Exemplar geschehen, nur leider stuemperhaft.

Ich habs dann mittels Software-Hack [checkm8-a5](https://github.com/synackuk/checkm8-a5) versucht die Startprozedur beim A5x Chip zu veraendern; hierbei wird der Code mittels Arduino IDE idealerweise auf ein **Arduino uno** geladen und mit einem *USB-Host-Adapter* ans iPad im DFU-Modus angeschlossen. Dann mit dem [ipad3Bypasser](https://alwaysappleftd.com/downloads.html) die RAMdisk gelöscht bzw. das Setup veraendert. Ggf. auch Sliver zu verwenden. Soweit die Theorie, klappt aber nicht mehr - apple hat wohl die Luecke gestoft. Hilft nur ein Ersatzboard aus China...

> [!NOTE]:
> es funktioniert doch, aber ueber Umwege mittels python-Skripte [iPro beta](https://alwaysappleftd.com/ipro_beta_program.html) und unter Zuhilfenahme von Sliver den SSH-part oeffnen und die Setup.app entfernen. Die Pfade in den sh-Dateien des iPro sind vermutlich anzupassen. Das Ganze via Mac.
