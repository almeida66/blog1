---
tags: OpenWrt
---
Ich bin so frei und habe die Listings aus [linux-magazin](https://www.linux-magazin.de/ausgaben/2022/02/wlan-mesh-teil-1) zwischengespeichert:

**5-GHz-Empfänger konfigurieren**
```
config wifi-device 'radio0'
option type 'mac80211'
option hwmode '11a'
option path 'soc/1b500000.pci/pci0000:00/0000:00:00.0/0000:01:00.0'
option htmode 'VHT80' # Kanalbreite
option channel '42' # Kanal
option country 'DE' # in Deutschland nur DE zulässig
option diversity '1' # automatische Antennenauswahl ein
option disabled '0' # Gerät nicht deaktiviert
```
**Einrichten des Mesh-Interfaces**
```
config wifi-iface 'mesh0'
option device 'radio0'
option ifname 'mesh0'
option mode 'mesh'
option mesh_id 'mesh-5ghz' # muss auf jedem MP gleich sein
option key '<I>Passwort<I>' # Passwort / Schlüssel
option mesh_fwding '1' # Mesh routet auch Nutzdaten
option mesh_rssi_threshold '0' # siehe Text
option encryption 'psk2/aes' # Verschlüsselung
option network 'lan' # identisch zur Angabe im AP
option disabled '0' # nicht deaktiviert
```
**AP im 2,4-GHz-Band:**
```
config wifi-device 'radio1'
option type 'mac80211'
option hwmode '11g'
option path 'soc/1b700000.pci/pci0001:00/0001:00:00.0/0001:01:00.0'
option country 'DE'
option htmode 'HT40'
option channel '9'
option diversity '1'
option disabled '0'
```
**Konfiguration des AP:**
```
config wifi-iface 'prod_radio1'
option device 'radio1'
option mode 'ap'
option ssid 'Die-supertolle-SSID'
option key '01234567890123456789'
option network 'lan' # wird gebridget mit 'LAN', identisch in 'mesh0'
option ieee80211w '1'
option ieee80211r '1'10
option mobility_domain '6f68'
option disabled '0'
option ft_over_ds '1'
option ft_psk_generate_local '1'
option encryption 'psk2' # WPA3 machte Probleme, siehe Text
```
