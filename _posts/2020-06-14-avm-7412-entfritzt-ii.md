---
tags: OpenWrt
---
## AVM 7412 entfritzt II
Es folgen die Angaben für den adblock-Addon.

Im Zusammenhang mit stubby werden Werbung und sog. Tracker auf DNS-Ebene gefiltert.
Hierzu werden die Pakete **adblock** und **luci-app-adblock** installiert. Eigentlich auch wget (zum Laden der Blocklisten), aber da ist/war wohl ein Problem mit den eingebauten Optionen, was zum Lade-Fehler führt.

Es wird ein neuer Reiter namens *Services* angezeigt. Hier (s.o.) die nächste Download-Utility über LuCi auswählen (fetch). Die Schnittstelle anpassen (lan oder wan) und unter Blocklist Sources die gewünschten Filter einstellen. Nicht alle, sonst geht vermutlich nix mehr.

Ein Enable Blocklist Backup ist vermutlich nicht verquert, damit im Falle eines Ausfalles wenigstens die alten Blocklisten verfügbar sind.

Unter *Scheduled Tasks* sollte man folgendes eintragen:
```
# Adblock Reload
45 05 * * * /etc/init.d/adblock restart
```
Hierbei werden täglich z.B. um 5:45h die Blocklisten neu aus dem Internet gelesen. Die cron und adblock Services neu starten...!

Man kann das DNS-Reporting via Tool "schöner" einstellen, muss aber nicht.

Das Ganze wurde über mehrere Artikel in der c't behandelt, aber von [Mike Kuketz](https://www.kuketz-blog.de/) in Form gepresst.
Einen grossen Dank an ihm.
