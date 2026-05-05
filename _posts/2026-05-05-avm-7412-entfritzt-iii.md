---
tags: OpenWrt
---
## AVM 7412 entfritzt III
Ich stelle grad um auf alte gemodette **unifi** [Geraetschaften](https://xdaforums.com/t/unifi-cloud-key-gen-2-plus.4664639/page-2) und jongliere mit den Tools herum; beim aktualisieren der FB habe - oder eher musste - ich eine komplette Neuinstallation durchführen, da der Versionssprung einfach zu gross war.

Weiterhin *adblock* installiert und dann *DDNs*; zusammen gabs Probleme: die meisten Anbieter verwenden **curl** als Updatevermittler, aber *adblock* hat in der aktuellen Version immernoch Probleme beim Laden der Blocklists. Unschoen... vor allem weil beide Tools unter OpenWRT tatsächlich auf 1x Funktion/Programm zugreifen, das wäre dann **fetch**. Funzt bei DDNs je nach Anbieter nicht. 

Aber was sehe ich: *adblock-fast* ist zwar ähnlich aufgebaut, aber wohl anderes Konzept. Bis auf das Neuladen der Blocklists scheint es recht *responsive* zu sein.
Und DDNs funktioniert nun auch. Ich brauche noch was anderes fuers wireguard...
> [!NOTE]
> Doof, zu spät entdeckt: die wireguard luci-app hat tatsächlich unter *global settings* die Option **curl** explizit zu nutzen.
