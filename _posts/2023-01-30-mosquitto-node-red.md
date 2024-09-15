Beide Programme sind Bestandteil der DTU-Auswertung, logischerweise aus open-source. Beim Testaufbau habe ich noch [dietpi](https://dietpi.com/) gewaehlt, da diese Programme bereits zum Bestandteil der Standardkonfig gehoeren.

Habe diese später auf einem Raspi0 zusammengefasst.

Man faengt mit dem sog. **MQTT** broker, namens [mosquitto](https://mosquitto.org/), an. Dieser bedient dann unter der eigenen IP den Port 1883. In der Konfig sollte man fuer interne Zwecke den *allow_anonymous* auf *true* stellen.

Danach folgt das Visualisierungs-Tool [node-red](https://nodered.org/); für das Einbinden der DTU, samt Weiterleitung an [thingspeak](https://thingspeak.com/channels/1969015).

Bei raspi-debian macht die Installation via **apt** Stress; moeglich dass das Paket fuer armhf nicht sauber ist.
Dafuer existiert auf github diese Variante via npm: `bash <(curl -sL https://raw.githubusercontent.com/node-red/linux-installers/master/deb/update-nodejs-and-nodered)`.

Danach stehen die Befehle: *node-red-start|stop|restart* zur Verfuegung; ggf. die Einbindung als systemservice, wobei besagter raspi-debian hier Berechtigungsprobleme aufwies. Der node-red wird ja nicht als root gestartet!
Danach steht dieser unter der IP und Port 1881 bereit.

In der c't [Ausgabe 03/23](https://www.heise.de/select/ct/2023/3/softlinks/y79g) wurde ein Listing fuers Hoymiles-solar bereitgestellt.
