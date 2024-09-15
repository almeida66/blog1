---
macintosh
---
## MacBook Air und DietPi
Eigentlich ist [DietPi](https://dietpi.com/) ein Betriebssystem fuer ARM, aber die haben auch UEFI/x86, ist ja eigentlich debian.
Somit koennte man die debian netinstall nehmen, oder halt das vorgefertigte von [DietPi](https://dietpi.com/downloads/images/DietPi_NativePC-UEFI-x86_64-Bookworm_Installer.iso.xz). Wichtig zu wissen: DietPi nimmt hier den Umweg ueber clonezilla und kopiert die Installationsumgebung erstmal auf die interne SSD. Parallelinstallation ist damit etwas ungeschickt.

Als Hardware steht hier ein MacBook Air4.1 mit nur 2GB; da kommt zwar xubuntu halbwegs zurecht, aber mit haeufigen Einfrieren mangels RAM. Also Dietpi, das noch einiges sparsamer ist.

Die Installation benoetigt Netzwerk-Zugang, Wifi wird vorab wegen dem verbastelten broadcom 43xx-Chip nicht erkannt. Also kommt entweder ein billiges USB-(Realtek)-Wifi- oder besser ein USB-to-Ethernet-Adapter zum Zuge. Zweiteres ist vorzuziehen, oder man muss die DietPi Startdateien vorher modifizieren.

Hat man Netzzugang, dann legt die Erstinstallation los, mit Frage-Antwort-Spiel. Bei mir kommt immer der midnight-commander MC dazu. Da es ja komfortabel sein soll, kommt eine Desktop-Umgebung (lxde) hinzu. Intel-HDA und pulseaudio. Falkon als browser ist dem Firefox vorzuziehen, dann ggf. andere Programme, je nach Nutzung.

Je nach verbautem wifi-Chip (hier bcm43224) werden linux-firmware-nonfree, firmware-sta-dkms, linux-headers-amd64 ggf. installiert und mit modprobe -r b43 b44 b43legacy ssb brcmsma bcma quasi entfernt und`modprobe wl aufgerufen.

Mit *dietpi-config* das Netzwerk mal antesten, ggf. neu starten. Den Netzwerk-Warte-flag entfernen, sonst haengt das Ganze beim Start.

Dann das leidliche Audio - ist zwar alles da, nur kommt kein Ton raus. Hier hilft tatsächlich *pulseaudio* zu installieren. Und  den passenden Lautstaerkeregler unmuten und schon geht das Audio... *Goodvibes* fuers audio-streamen und *cheese* fuer die Cam - fertich.

Fast, ggf. noch die Funktionstasten anpassen, da dort der MacBook einige Funktionen hinterlegt (/etc/default/keyboard) oder halt via *dietpi-config*.

Wenn man nicht zig-Tabs im browser offen hat, dann bleibt noch RAM ueber und das System friert nicht ein. Unschoen, aber mit MacOS ist das Arbeiten mit alter Software eine Zumutung, und das MacBookAir ist dafuer in Benutzung fuer kleinere Administrationsaufgaben im lokalen Netz oder halt als Surfmaschine... 
