---
tags: hardware
---
Ist eigentlich ein Skript, ich packe es dennoch unter *hardware*. Hat was mit Solartechnik zu tun, naemlich die Datenanbindung an die Growatt noah2000 Speicherbatterie, die mit WiFi die Daten streut.
Der Hersteller will natürlich sein eigenen Kram anbieten, aber wozu...

Das [Skript](https://github.com/mtrossbach/noah-mqtt) liest die API-Daten aus und kann diese an einem broker, wie mosquitto, weiterleiten. Den Rest besorgt dann node-red, o.ä.

Unter linux kann man das Skript im home-verzeichnis, oder gleich in die */usr/sbin* packen - je nach Derivat. Aufruf erfolgt via `GROWATT_USERNAME=myusername GROWATT_PASSWORD=mypassword MQTT_HOST=localhost MQTT_PORT=1883 ./noah-mqtt`

Ggf. ein cron-job aufsetzen oder unter init.d als Startoption einbinden.

Die anschliessende Anzeige im mosquitto ist mehr als ausreichend, um alle möglichen Verbrauchsdaten anzuzeigen.
