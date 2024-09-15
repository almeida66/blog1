Wozu in die Ferne schweifen? Habe daheim 2-3 Mini-server am werkeln, die über ddns in die weite Welt wollen. Die ueblichen Router sind da sehr eigen mit der Portvergabe und kennen fürs http nur 80 und 8080.

[Lighttpd](http://www.lighttpd.net/) kommt dann zur Hilfe und hostet dank vhost mehrere Seiten und siehe da, dank **mod_proxy** auch einen halbwegs nuetzlichen **reverse-proxy**. Damit kann man mit den wenigen offenen Ports den Datenfluss umleiten. 
