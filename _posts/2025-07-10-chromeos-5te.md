---
tags: libreboot
---
## ChromeOS, die 5te
Ja, man(n) kann es nicht lassen. Was verscheberln die diese auch. Diesmal mal eher was relativ Neuwertiges, ein ACER 314-4H mit satten 8GB RAM und 128eMMC und einem intel N100. Ich würde sagen aktuell der schnellste aus der Sammlung.
Ok, hier würde ChromeOS tatsächlich noch einige Jahre Support bieten, aber wer will schon seine Daten der "US-Cloud" anvertrauen...

Es handelt sich hier um den [CRAASNETO](https://docs.mrchromebox.tech/docs/supported-devices.html) und wird von [mrchromebox](https://docs.mrchromebox.tech/) unterstuetzt, ein sog. Alderlake. Wie immer gehört der Rechner in *Developermodus* und etwas trikky die neuen Sicherheitschips Ti50, die neuerdings verbaut werden. Hier hilft nur eine seltasame Prozedur in der root-CLI.
Dabei wird via Ctrl+Alt+F2 die Kommandozeile gestartet und als root (ohne Passwort) angemeldet. Mit `gsctool -a -I` kann man sich die aktuelle Einstellung angucken, interessant ist hier **AllowUnverifiedRo**

Um diese auf *AllowUnverifiedRo:always* zu setzen muss mittels [Aufruf](https://www.chromium.org/chromium-os/developer-library/guides/device/ro-firmware-unlock/#purpose-of-this-guide) `gsctool -a -o` das Ganze gestartet werden und mit der Powertaste *bestätigt* werden. Und wenn "Another press will be required" erscheint, dann abwarten und **NICHT** die Powertaste drücken, nur wenn wieder "Press PP button now" angezeigt wird; das geht so ein paar Minuten hin-und-her mit Wartezeiten. Sollte es geklappt haben, dann fährt der Rechner runter und aktualisiert sich (hoffentlich). Wieder in den Developermodus setzen, root-CLI öffnen und `gsctool -a -o AllowUnverifiedRo:always`eingeben und mit der Powertaste *bestätigen*. Mit `gsctool -a -I` prüfen; bei der Gelegenheit noch den Schreibschutz mit `gsctool -a -w disable` aushebeln und ebenfalls bestätigen.

Danach als *chronos* die Kommandozeile starten und bekannte Prozedur `cd; curl -LO mrchromebox.tech/firmware-util.sh && sudo bash firmware-util.sh` lostreten. Das **WP** sollte nun disabled sein und je nach gusto RW_LEGACY oder gleich die full_ROM flashen. Für alle Fälle ein USB-Stick für die Sicherheitskopie der originalen Firmware bereithalten. *Reboot* tut gut.

Danach mittels USB/SD-Karte das neue OS installieren. 
