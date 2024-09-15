---
tags: macintosh
---
Alleine mit Mac System 7 ist es noch nicht getan; es fehlt die allg. Apple Netzwerksoftware und MacTCP. Und nicht zu vergessen die passende Hardware, hier eine Farallon Netzwerkkarte für die LC-PDS Schnittstelle (gabs in USA für wenig Geld).
Alles da, Kartensoftware eingespielt, Einstellungen probiert und "ping": es ist ansprechbar... (nicht ganz, wenn kein Dienst läuft, dann auch keine Antwort).
Für die sog. Addons (oder nur zum Einlesen) empfehle ich die Seiten von Tyler Stable [macman](http://web.archive.org/web/20141113164228/http://www.fenestrated.net/~macman/mac/).

Welcher webserver denn nun? Viele gibt es ja nicht für 68k Macs, sollten auch nicht den Arbeitsspeicher völlig in Beschlag nehmen... Nun, die Wahl fällt zwischen den frei verfügbaren MacHTTP (später kommerziallisiert, als Webstar) oder NetPresenz. Letztere hat noch den Vorteil nen guten ftp-Server zu beherbergen und kann cgi. Ich empfand allerdings die web-Konfiguration und die Zwangsverwendung von AppleShare etwas unvorteilhaft.
MacHTTP bietet dafür kein cgi (nur unter Verwendung von MacPerl), ist aber sehr leicht und komfortabel zu bedienen. Man sollte die Security-Einstellungen nicht vergessen...
Die Verwedung von Arbeitsspeicher liegt nun bei ~1850kB + MacHTTP. Hierbei wurde statt dem ncsa-telnet doch das alte FTPd (NetPresenz) als ftp-Server verwendet, da ersteres irgendwie Aussetzer oder vergesslich(?) war/ist. 
