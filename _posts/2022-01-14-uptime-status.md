---
tags: ARM
---
Ein recht interessantes mini Tool zur "online" Status-Server-Ueberwachung, namens [update-kuma](https://github.com/louislam/uptime-kuma); wichtig wenn mal wieder Stromausfall oder sonstige nervige Ausfaelle unbemerkt stattfinden.

Das Ganze natuerlich miniaturisiert auf einen RasPi0W wird schwierig, aber auf den neueren RasPi2W sollte das klappen. Probehalber schon mal auf einen RasPi3B ausgetestet.

Die 32bit Version duerfte Probleme bereiten, aufgrund der nicht ganz so aktuellen notwendigen Programmquellen zu docker oder node.js.

Erstmal das Lieblings-Linux [Debian](https://raspi.debian.net/) fuer den passenden Raspberry Pi in Form eines vorgefertigten Images fuer **armel** oder besser **arm64** runterladen und via *dd* oder *balena-etcher-tool* auf die SD-Karte verbannen.
Beim Erststart wird die SD-Karte automatisch vollstaendig zur Nutzung vorbereitet; LAN funktioniert via dhcp, WLAN muss nachtraeglich unter *interfaces.d* mit den eigenen Zugangsdaten gefuettert werden. Ein `ifup wlan0` hilft.

Ich habe vermutlich die schwierige Variante ohne docker installiert; naemlich ueber den **nvm-installer**. Das geht aber auch direkter mit:
`curl -sSL https://deb.nodesource.com/setup_1y.x | sudo bash` [y=akt. Index!]

danach ein `apt install -y nodejs` ; anschliessend ein Test mit `node --version bzw. npm --version`.

Irgendwann sollte man dann uptime-kuma via git klonen: `git clone https://github.com/louislam/uptime-kuma.git` und im Verzeichnis `npm run setup` aufrufen.

Den Rest nach Belieben mit **pm2**, als service oder mit forever bzw. nohup, ...
