---
tags: ARM
---
ARMv6 geht wohl gar nicht; mit **docker** erhaelt man einen "Maschinenfehler", ich nehme an die CPU hat irgendein Befehlssatz nicht parat; für **nodejs** wird min. v14 abverlangt, und das wird fuer armv6 nur noch [inoffiziel](https://unofficial-builds.nodejs.org/download/) bereitgestellt und offenbar nicht vollstaendig unterstuetzt.

Somit blieb ARMv7 ueber, in Form eines [BeagleBoard-xM](https://beagleboard.org/beagleboard-xm). Es hat zwar kein Wifi, dafuer LAN.

Diesmal als debian buster via
`curl -sSL https://deb.nodesource.com/setup_14.x | sudo bash und einem apt install -y nodejs`.

**npm** wurde anschliessend aktuallisiert; geht doch. 
