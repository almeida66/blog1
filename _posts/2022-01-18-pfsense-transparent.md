Da ich es selber immer wieder vergesse und das [pfsense](https://docs.netgate.com/pfsense/en/latest/bridges/index.html) System nicht jeden Tag administriert wird:

1. Unter dem Reiter *Firewall* **Disable Outbound NAT** wählen
2. Unter *System/Advanced* jeweils **net.link.bridge.pfil_bridge** bzw. **_member** umstellen *[1 bzw. 0]*
3. Unter *Interfaces/Bridge* eine neue **Bridge** erstellen (WAN+LAN)
4. Bei *Interfaces/Assig* die neue bridge in die Konfiguration *addieren*
5. Das neue Interface *aktivieren* und eine **statische Adresse** + Gateway vergeben
6. Bei *Services* ggf. vorhandene DHCP(v4+6) **inaktivieren**
7. Bei *Interfaces* LAN+WAN jeweils auf **none** stellen und Filter entfernen
8. Bei *Firewall* die Grundkonfig für WAN erstellen: **IPv4+6 * pass**
9. Bei OPT1 IPv4 für **OPT1 net** auf **pass** setzen

Ueber *backup/restore* kann man sich die Filterregeln+Aliases etc. aus einer alten Konfig laden.

Danach die ueblichen Services einschalten usw. usw.
