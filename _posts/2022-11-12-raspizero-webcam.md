---
tags: ARM
---
Fuer irgendwas sollte der der Raspi 0w doch gut sein; da der Wlan-Chip eher instabil ist, kam die Idee mit dem PiCam-Aufsatz fuer eine webcam, die nur alle paar Stunden startet [^note].
Ich hatte Glueck und habe noch die v1.x Version erhalten. Die 2er leidet je nach Charge wohl an Fertigungsproblemchen mit dem Fokus...

Hier wurde kurzerhand das leichtgewichtige [Dietpi](https://dietpi.com/) installiert.

Mit raspi-config wird die Schnittstelle aktiviert, damit diese beim Neustart zur Verfuegung steht. Der Raspi wird ganz normal fuers wlan eingerichtet.

Fuer Fotos genuegt die Verwendung von **raspistill**, z.B.
`raspistill -h 640 -w 480 -awb horizon -roi 0.40,0.36,0.25,0.3 -rot 90 -q 90 -n -o $opath`

- h/w - steht fuer die Bildgroesse
- awb - sowas wie "Voreinstellungen": sonne, horizont, nacht, strand, ..
- roi - wer nur ein Teil der Sensorflaeche nutzen will: 0-1.0,0-1.0
- rot - Rotation in grad
- q - Bildqualitaet
- n - keine Vorschau
- o - Speicherort

Die Pfadvariable verweist auf eine jpg-Datei, irgendwo im home-Verzeichnis.
Danach folgt die Weiterleitung zum web-server via **curl** und **ssh-ftp**:
`curl -k "sftp://$HOST/public_html/" --user "$USER:$PASSWD" -T "/home/VERZEICH/Datei.jpg"`

Das Ganze in einem ausfuehrbaren [Skript](https://www.pcwelt.de/article/1166835/webcam-mit-raspberry-zero-pi-w-einrichten.html), der via cron alle paar Stunden aufgerufen wird.

[^note]: das Ganze arbeitet auf der [Wetterseite](http://weather-server.uk.to:8080/)
