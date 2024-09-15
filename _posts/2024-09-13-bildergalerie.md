---
tags: allgemein
---
## Foto-Cloud
da hat [heise](https://www.heise.de/select/ct/2024/19/2419711144883730226) wieder eine umsetzbare Idee fuer wenig Geld aufgezeigt.

Das Ganze funktioniert mit [immich](https://github.com/immich-app/immich) und wird unter docker aufgesetzt. Docker habe ich bis heute nicht verstanden, aber die Installation erfolgt zum Glueck via [Skript](https://ct.de/ynx4).

Statt RasPi habe ich die aktuell guenstigeren [Radxa](https://wiki.radxa.com/Rock3/3a) gewaehlt, mit 4GB RAM. Aufgrund der Datenmenge macht eine externe SSD eher Sinn. Trotz der vorhandenen M.2 Schnittstellen, habe ich der NVMe-SSD ein Umgehause verpasst und an USB3 angeschlossen.
Wie immer kommt bei mir [DietPi](https://dietpi.com/) zur Verwendung, ein debian-Derivat fuer ARM. Der Start war knifflig, da ist der Netzwerk Anschluss des Radxa, alias der zug. Treiber, etwas unzuverlaessig.

Dann kommen die Installations-Skripte aus der ct zur Anwendung:
```
curl -fsSL https://get.Docker.com -o get-Docker.sh
sudo sh get-Docker.sh
```
User umgruppieren:
```
sudo usermod -aG docker $USER
newgrp docker
```
Und docker testen:
`docker run hello-world`

Und hier erstmal **stoppen**; ja, viele Wege fuehren nach Rom... Unter debian wird das Verzeichnis unter */var/lib/docker* angelegt. Keine gute Idee fuer eine sd-Karte... Wir mounten somit die externe SSD und binden diese via fstab ein. Dann wird das gesamte docker-Verzeichnis auf die SSD verschoben. Ich hab das Verzeichnis dann via Symlink angelegt; man kann auch direkt die SSD dort einbinden usw usw
Unter */etc/docker* wird noch eine daemon.json erzeugt mit:
```
{
"data-root": "/verzeichnis/docker"
}
```

Wenn docker dann wieder gestartet wurde und den Kram anlegt, dann schon mal den GUI [portainer]( https://hub.docker.com/r/portainer/portainer) vorbereiten:
`docker volume create portainer_data`

Und nun den mega-Befehl:
`docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest`

Die Ports kann man bei Bedarf veraendern, lassen wir aber besser so... Die Installation benoetigt eine Weile.
Dann via web die portainer-Seite unter Port 9443 aufrufen und sich erstmals anmelden. Danach ein neuen Stack (immich) anlegen und die Beispieldateien (docker-compose.yml und example.env) aus [immich](https://github.com/immich-app/immich/tree/main/docker) verwenden; ersteres um *stack.env* korrigieren.
Idealerweise mittels *Duplicate/Edit* beim **immich_server** unter *Volumes* den Container-Pfad fuer den Upload auf die externe SSD umleiten. Das Ganze nochmals neu veroeffentlichen.

Nun sollte die graphische Oberflaeche unter Port 2283 bereitstehen; dort den Admin anlegen und die User.

> [!NOTE]
> Mit [tailscale](https://tailscale.com/) in der freien Version erreicht man auch immich von Aussen via vpn erreichen
