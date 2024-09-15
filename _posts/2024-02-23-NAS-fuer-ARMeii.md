---
tags: ARM
---
## NAS fuer ARMe ii
Wenn man mit der Vorarbeit fertig ist, wird die Hardware zusammengeschraubt, hier halt 2x2,5"-HDD, die ueber waren und damit ein RAID1 zusammengestellt.
Auch hier die Angaben aus OpenWrt zu [NAS](https://openwrt.org/docs/guide-user/services/nas/start) und anschliessend die speziellen nfs-Dokus.
Idealerweise alles via putty und der Kommandozeile; die paar Packages werden via opkg bereitgestellt:
```
opkg kmod-usb-storage kmod-usb3 nfs-kernel-server nfs-kernel-server-utils kmod-loop mdadm
```
Das eine oder andere wie hdparm oder smartctl kann ja nachgeladen werden; vielleicht noch nsfv4. Unter */etc/exports* wird der Server samt MountPoint angegeben.
>[!NOTE] hier wird ein RAID gebastelt, somit wird aufgrund der OpenWrt-Datenstruktur unter */mnt/data* ein lesbares Verzeichnis mit `chmod -R a+rw /data` schreibend gemacht und unter bei Bedarf */etc/init.d/boot* mit mkdir nachgetragen.

Warum? Weil hier das root-Verzeichnis quasi imaginär gebildet wird und beim booten neu aufgebaut. NFS, alias mdadm, benoetigt beim booten den Pfad, sonst bleibt es haengen und damit kein RAID.
[mdadm](https://docs.linuxfabrik.ch/software/mdadm.html) ist dann auch etwas umfangreicher in der Installation (hier: 2xHDD mit RAID=1):
`mdadm --create /dev/md/name /dev/sda1 /dev/sdb1 --level=1 --raid-devices=2`
Ueblicherweise wird das /dev/mdx angegeben, je nach System (hier OpenWrt!) in der */etc/fstab* und/oder MountPoint, aber nicht mit der *uuid* bekannt machen.
Anschliessend die mdadm.conf erzeugen: `mdadm --detail --scan > /etc/mdadm.conf` .
Ein `mdadm --assemble /dev/mdx` startet den Server, ggf. mit `cat /proc/mdstat` nachschauen was abgeht. Auch ein `mdadm -D /dev/mdx`ist behilflich.
Und letztlich: `sudo exportfs -ra`. Um den RAID-Verbund als normales Speicherlaufwerk zu nutzen, muss noch ein Dateisystem mit `sudo mkfs.ext4 /dev/mdx` drauf.

Danach Client-seitig ein linuxoides `mount -o nfsver=3 <IP>:/mnt/data /home/user/nfs` oder was auch immer. Die optionale Eingabe der Version kann - muss aber nicht - notwendig sein. Je nach Client. Obiges ist **ein** Konfig-Beispiel; es fuehren mehrere Wege dahin... 
