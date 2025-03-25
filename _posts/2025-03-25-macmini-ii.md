---
tags: macintosh
---
## Mac mini ii
Ja, es geht weiterhin um **proxmox**, alias dem Clusteraufbau mit 2x Mac mini + Qdevice. Der Macmini als unibody hat bereits ein eingebautes Netzteil, also wurde kurzerhand ein 2tes Exemplar geholt. 

Mit dem Erscheinen der Mx-Versionen werden diese quasi verschenkt. Naja, Core2duo ist ja nicht wirklich flott, aber fuer Privatanwendungen voellig ausreichend. Kurzerhand eine SSD-SATA samt mehr RAM (aktuell 8GB) beordet und eingebaut. Den (proxmox)[https://www.proxmox.com/en/downloads] Installer kann man direkt verwenden, ohne den Umweg (eh debian-basiert) ueber Debian-Installation zu nehmen.

Am besten eine statische IP-Adresse vergeben um den 2ten Node (macmini) entsprechen zu konfigurieren. Unter *datacenter* wird ein Cluster mit ent. *fingerprint* erzeugt. Diesen muss man im 2ten Node nach *join cluster* eintragen. Mittels ssh verbindet sich das Ganze, nach einer Weile taucht der Icon des 2ten Macmini im "1" auf. Die GUI-Oberfläche ist dann nur eine!

Damit der Spass auch Sinn macht sollte ein Backup-Server in Form einer NAS o.ä. zusaetzlich aufgesetzt werden; damit wird zudem ein Quorum (Mehrheit) aufgesetzt, um Entscheidungen zu faellen - das sog. **qdevice**.

Als qdevice wird kurzerhand ein aufgemotzter (radxa 4c+)[https://radxa.com/products/rock4/4cp/] mit satten 4GB, Gigabit Ethernet und USB-3 mit einem minimal-(ARMbian)[https://www.armbian.com/rockpi4/] aufgesetzt. Als NAS kommt das schlanke (openmediavault)[https://www.openmediavault.org/] in Frage. Mittels vorbereitete Skripte kann man das Ganze auf der Kommandozeile automatisiert ausführen:
'wget -O - https://github.com/OpenMediaVault-Plugin-Developers/installScript/raw/master/preinstall | sudo bash'

Ein reboot tut gut - danach folgt die eigentlich Installation mit:
'wget -O - https://github.com/OpenMediaVault-Plugin-Developers/installScript/raw/master/install | sudo bash'
Es dauert schon eine Weile, da etliche binaries geholt und installiert werden. Irgendwann kommt die Info sich doch via Browser bei der IP-Adresse anzumelden.

Ich nutze hierbei eine am USB-3-port angeschlossene NVMe-disk; etwas trikky damit diese von OMV erkannt wird. Man sollte diese schon *mounten*, vermutlich ist das aber systembedingt.
Egal, auch hier eine statitsche IP-Adresse verpassen und unter *Storage* die neue NVMe einbinden, ggf. das filesystem erzeugen. Da diese als gemeinsames **backup** dienen soll, wird das Laufwerk *ge-shared* und z.B. via NFS bereitgestellt. Zugriffsrechte noch vergeben.

Nachdem alle Geraete an einem Hub haengen - im gleichen Netzwerk - folgt Teil 2: In promox dann unter **Backup** das NSF-Laufwerk mittels IP-Adresse bekanntgeben; fuer beide Nodes freigeben.

Auf der Kommandozeile beider Nodes wird 'apt install corosync-qdevice' ausgeführt. Im Qdevice - alias radxa 4c+ - 'apt install corosync-qdevice corosync-qnetd' installiert. Soweit so gut, dann folgt im Cluster (Macmini 1) der Aufruf 'pvecm qdevice setup <IP-Adresse radxa/qdevice> -f'. Im ARMbian ist eh ssh und root-Zugang eingerichtet - wichtig - damit erfolgt die Konfiguration des Quorums.

'pvecm status' sollte dann die Nodes und *Votes* anzeigen, ggf. 'systemctl status corosync' zur weiteren Prüfung eingeben.
