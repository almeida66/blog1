---
tags: OpenWrt
---
Ich weiss gar nicht wie anzufangen. Eigentlich war der Plan aus meiner alten parallelport Webcam von Creative Labs mit einem ThinClient ein Webcamserver aufzubauen. Bei der Suche stolperte ich immer wieder über <http://www.openwrt.org> und Minirouter wie z.B. der TL-MR3020 (baugleich mit TL-WR703N).
Also her damit, so teuer war die Hardware nicht und zur Not kann man diese noch anderweitig nutzen.

Dank sehr geringem Stromverbrauch ist der TL-MR3020 ideal für solche Vorhaben. Zunächst wird die passende Firmware aufgespielt und dank des Lua-GUI ist die Installation relativ einfach.
Grob kann man bei USB-Webcams zwischen UVC- und GSPCA-Treibermodule unterscheiden. Erstere sollte auf jeden Fall den Vorzug gegeben werden. Zudem ist es ratsam den Status unter <http://www.ideasonboard.org/uvc/> für die jeweiligen Modelle vor dem Kauf zu prüfen. Eine preiswerte UVC-Webcam mag zwar unter Win funktionieren, aber leider nicht unbedingt unter Linux. Die erste hama-Webcam war ein Reinfall. Ich habe mir zu diesem Zweck dann eine Logitech C210 besorgt, die funktionierte auf Anhieb.
Gemaess der Info-Seite unter OpenWrt sind diverse Module zu usb-video notwendig und mjpg-streamer. Damit kann man ein "Dauerbild" erzeugen und das Ganze dem zug. http-Server bereitstellen.

Das war nun die eine Möglichkeit, ich wollte aber alle paar Minuten Aufnahmen zu einem externen Server senden. Die Lösung war wput (statt wget); damit werden in einem batch-Script die Aufnahmen per ftp auf das Homepageverzeichnis übertragen.
Das Ganze wird beim Start dem Router als Befehlskette (`mjpg_streamer -i "input_uvc.so -d /dev/video0 -f 5 -r 640x480" -o "output_file.so -d 600000 -f /www/webcam -s 1 -c /usr/bin/wput-provider.sh"`) mitgegeben. Hierbei wird eine Zeitvorgabe, Ablageort, Anzahl Aufnahmen und der Verweis auf den batch-Script angegeben.
Der TL-MR3020 selbst wird als WLAN-Client konfiguriert und hat über das Netzwerk Verbindung zur Aussenwelt. Ggf. ist auch ein Eintrag über Dyndns möglich.
