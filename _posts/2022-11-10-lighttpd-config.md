[Lighttpd](https://www.lighttpd.net/) kommt leicht geaendert daher bzw. die Konfigurationsdateien verteilen sich.
In der *lighttpdconfig* werden stellenweise nur die Verzeichnisse und Port angegeben; der Rest ist tuning-Kram. Zudem hier versteckt die logs- und dirlisting-Angaben.

Wichtiger wird die *modulesconfig*:
- mod_access
- mod_alias
- mod_proxy
- mod_fastcgi
- mod_cgi
- mod_simple_vhost

In der **conf.d**, unter *cgi* und *fastcgi* werden die .pl und .cgi Pfade korrigiert. Gleiches fuers php-socket unter *fastcgi*.
**Dirlisting** wird *"enabled"*, wegen der Nutzung des usb-stick-Verzeichnisses.

Unter **proxy** wird der extra Port via `$HTTP["host"]` angegeben.

Unter **simple_vhost** der standard web-Zugang, der Rest findet in **vhosts.d** statt.

Dort wird es kryptisch:
`$HTTP["host"] == "(name1\.domain\.tld|name2\.domain\.tld|name3\.domain\.tld)$" {
simple-vhost.server-root = "/var/www/xxx"`

und
```
$HTTP["host"] == "name1.domain.tld" {
server.document-root="/var/www/name1.domain.tld" }
$HTTP["host"] == "name2.domain.tld" {
server.document-root="/var/www/name2.domain.tld" }
$HTTP["host"] == "name3.domain.tld" {
server.document-root="/var/www/name3.domain.tld" }
}
```
Und zu guter letzt die log-Dateien am Ueberlaufen hindern via **logrotate** oder hier unter */etc/newsyslog.conf*
