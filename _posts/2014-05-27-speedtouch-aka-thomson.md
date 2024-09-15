---
tags: router
---
Mittlerweile in Deutschland nicht so ganz verbreitet, aber gut; zumindestens was die Chips angeht, nämlich Broadcom - die für schwierige Leitungen. UND nicht so geschwätzig wie die FritzBoxen...

Der Beitrag ist eher für meinen Gebrauch gedacht (lange habe ich gesucht); der Nachteil an den Thomson-Routern ist die GUI-Software - keine Worte. Dafür ein extrem mächtiges CLI auf Kommandozeile.

Hier explizit ein Beispiel einer Weiterleitung zwecks dynamisches DNS:
```
=>service host add name HAMA mode server
=>service host rule add name HAMA protocol tcp portrange 8081
=>service host assign name HAMA host 192.xx.yy.zz
=>saveall
```
Warum das Ganze? Bei meiner Zusammenstellung wurde der BeOS-webserver nicht im GUI angezeigt; somit keine Möglichkeit diesen per GUI als solchen zu konfigurieren.
