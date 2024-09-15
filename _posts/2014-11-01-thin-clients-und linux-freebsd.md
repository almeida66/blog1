---
tags: thinclients
---
## thin clients und linux/FreeBSD
Hier möchte ich kurz auf eine sog. Hardware-Firewalllösung auf Basis von Linux/FreeBSD. Der Vorteil ist u.a. dass das home-Netzwerk mit den ganzen Rechnern "physisch" vom WWW getrennt sind.

In heise wird u.a. eine einfache Netztrennung mit DMZ beschrieben, wofür man nur einen Zusatzrouter benötigt. Hier gehe ich halt weiter und hänge dazwischen einen Thin Client mit pfsense als Firewall ein. Idealerweise sollte dieser 2 Netzwerkports haben oder zumindestens noch einen Steckplatz oder USB für ein Netzwerkadapter besitzen. Empfehlung: Wyse 9450XE. Hier ist ein PCI-Steckplatz vorhanden und hat 2 IDE-Schnittstellen.

Ich verwende eine CF-Karte mit 1 bzw. 2GB, reicht vollkommen aus. 
Hierzu stellen die Entwickler von pfsense passende ISO-Dateien zur Verfügung. Diese sollte man auf CD brennen und mit einem externen Laufwerk auf die CF-Karte installieren. Thin Clients älteren Baujahrs sind bei der Auswahl der Bootmedien etwas eigen :) Die notwendigen Kabeladapter hierzu findet man günstig im Internet.

Man sollte die CF-Karte im Format ext2 formatieren und die Installroutine starten. Hierbei werden die Netzwerkarten abgefragt und in externe (www) und interne (home) angegeben. Ggf. noch die Netzwerkadresse anpassen, aber das kann man noch später im WebGUI nachholen. Das ist durchaus ein Vorteil, da doch eine Unmenge an Einstellungen möglich sind. Es gibt im howto-Bereich dieser Software die Einstellung einer "transparenten Firewall", die ich hier empfehle. D.h. die hängt im Netz und wird nicht "gesehen". Zur Einstellung der Firewall-Regeln sollte man gängige Foren/Howtos lesen und diese im System freigeben (POP3, IMAP, HTTP, ...).

Wenn alles korrekt verdrahtet und eingeben ist, sollte man den Thin Client ins Netzwerk ein binden und den einen oder anderen Security-Test starten.

Viel Erfolg
