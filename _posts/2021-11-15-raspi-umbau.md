---
tags: hardware
---
Statt ThinClients nutze ich nun auch die kleinen [Raspberries](https://www.raspberrypi.org/) Pi; einen als [RiscOS](https://www.riscosopen.org/) Server, einen als RiscOS-[netbook](https://www.riscosbits.co.uk/portables.htm) via motorola lapdock und nun einen als [gopher](https://de.wikipedia.org/wiki/Gopher) Server.

Die Kleinen (RP zero) haben z.T. kein Netzwerk-Anschluss, kosten dafuer nur 5Euro (je nach Anbieter).
Der Umbau lohnt inzwischen nur wenn man bereits USB-Netzwerk-Dongles rumliegen hat - wifi oder ethernet. Ueblich sind immernoch die Realtek, die problemlos erkannt werden.

Auch die RP0 haben einen OTG-Anschluss, den kann man via Kabel oder halt Loetung direkt auf die Pins auf der Unterseite anbringen. Das Ergebnis ist eine sehr kompakte Bauweise.

Man nehme also +5V, GND, sowie D+ und D- des USB-Dongles und auf P1, P6, sowie P22 und P23 des RP0.
