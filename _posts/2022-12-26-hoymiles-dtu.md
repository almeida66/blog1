Unser Neuzugang, eine Balkon-Solaranlage, klassisch mit ca. 740W, wurde mit einem hoymiles 600 Wechselrichter beliefert. Der Aufbau war jetzt nicht so wild, habe allerdings doch ein Wieland-Stecker samt extra Leitungssicherung B10 verwendet. Ein 2-poliger FI lag auch noch rum.

Die Sonne scheint und es blinkt, aber fuer Auslesen werde ich kaum weitere 150€ hinblaettern.

Das gibts auch als [OpenDTU](https://github.com/tbnobody/OpenDTU) (oder halt [ahoy-DTU](https://ahoydtu.de/) fuer den ESP8266); das war zufaellig ein Bericht in der c't [24/22](https://www.heise.de/select/ct/2022/24/2224315343257577596).

Der **Wemos D1** lag noch rum, fehlte nur noch das Funkmodul in Form des **NRF24L01+**[^note]; hier unbedingt auf das "+" achten. Der ohne funktioniert nicht.

Die 8 Litze sind schnell zusammengesteckt und da fehlt dann nur noch die Firmware. Die ist bei github vorhanden und kann via ESP-Flasher geladen werden.

Dann *reboot* und nach dem Zugang *192.168.4.1* suchen; dort die passende Eintraege furs lokale Netz, die Seriennummer des Wechselrichters, samt Panels, eingeben und schon ist man fast am Ziel.

Beide Systeme unterscheiden sich alleine durch den Chip: entweder ESP32 oder halt ESP8266. Der Output ist voellig ausreichend. Wer jetzt diesen weiterverarbeiten will, dann kommen u.a. die broker-Software **mosquitto** und die Visualisierungs-Software **node-red** in Frage.

[^note]: hier noch D2 (CE) und D1 (IRQ) beachten - typanhängig; ein Update hat mir diese Einstellungen zerschossen
