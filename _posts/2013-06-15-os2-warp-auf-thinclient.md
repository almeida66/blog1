---
tags: thinclients
---
## OS/2 warp auf thinclient
Ja, dieses Betriebssystem lebt noch weiter, zumindestens mit aktualisierten Treibern als <http://www.ecomstation.com>.
Tatsaechlich habe ich noch eine original-CD einer damaligen Vobis Aktion. Und das Ganze sollte nun auf den ThinClient aufgespielt werden und ggf. als WebServer dienen.
VIA wurde bekanntlich unterstützt, aber die restliche Hardware ...(?) hier: Wyse 941GXL mit 1GHz und 512MB RAM.

VIA C3 Nehemiah startet mit der eCS 2.0 und OS/2 Warp 4.x, VIA Geode dagegen nicht und bricht sofort ab. Die restliche Hardwareerkennung ist zwar zweitrangig, wird aber mit aktualisierten Treibern vollständig erkannt. Ich verwende nun eine modifizierte Boot-Cd mit den Treibern von Daniela Engert (Danixxx) und der Rest wird via CD nachträglich eingebunden.

Problematisch ist halt USB, da friert das System immer ein - liegt es am Treiber?
Zudem wird beim Laden schon mal das eine oder andere Bit vergessen; entweder ist die CD etwas beschädigt oder der Prozessor ist halt zu schnell für die Software.

Ach ja, das Ganze lässt sich auch unter Virtual PC oder VMWare installieren. Ich warte noch auf eine alten ThinkPad, dann gehts richtig los ;))

Der Thinkpad ist nun da, OS/2 dank IBM-eigene Bootdisketten ohne viel Probleme installiert und ein paar nützliche Programme geladen. Kleiner Schönheitsfehler: der [ThinkPad 390](http://thinkwiki.de/390) hat kein Netzwerk. Und nu? Wie soll ich über VNC den Server "stillvoll" ansprechen?
Moment, da ist doch noch ein Modem als mini-PCI... war da nicht was im [ThinkPad Wiki](http://thinkwiki.de/WLAN_nachr%C3%BCsten)?
Man kann statt der Modem-Karte einfach eine Wlankarte einbauen und eine Antenne nachrüsten. Hier sollen die Intel Pro/Wireless oder Atheros aufgrund der Treiber vorrangig verwendet werden.

Mittels GenMac und Xwlan werden die nötigen Treiber installiert. In OS/2 immer etwas mühsam. Die Karte wird erkannt, irgendwie sucht das Wlan noch "Anschluss", aber es ist da...
