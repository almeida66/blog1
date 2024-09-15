Bin gerade dabei einen alten Compaq Armada M700 mit Linux zu bevölkern und teste dabei die unterschiedlichen Distributionen aus, die mit wenig Hauptspeicher auskommen.
Zunächst natürlich [puppylinux](www.puppylinux.com), wobei hier aus Entwicklungszwecken die alte Version 4.12 eingerichtet ist und parallel dazu die neueste Wary 5.2.90 erfolgreich arbeitet.

Diese kleinen Distris kommen mit wenig Festplattenspeicher aus, dadurch wird eine 40GB-HD in mehreren Partitionen aufgeteilt und startet dank grub jeweils von der ersten aus. Wenn kein vernünftiger install-script vorhanden ist, kann die alte Methode "Harddisk upgrade min howto" verwendet werden; hierbei wird mit `cp -a /verzeichnis-live /mnt/hdd` die gesamte Umgebung kopiert und anschliessend in /grub/menu.lst der Eintrag ergänzt. Meistens klappt auch alles auf Anhieb.

So, nun habe ich etliche Distris ausprobiert, von Gentoo, Crux, Arch, Porteus, Zeven, Flux, Crunchbang, SliTaz und noch einige andere. Für meinen alten Compaq M700 hat sich [antix](antix.mepis.org) als die ressourcenschonendste und mit alter Hardware gut auskommende Distri herausgestellt. Diese basiert auf Mepis, einem Debian-Derivat. Meine Empfehlung!
