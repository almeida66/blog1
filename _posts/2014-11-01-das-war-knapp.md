Puh, und ich sach noch *never change a running system*...

Ich meinte es ja nur gut und will/wollte etwas energiesparendes einsetzen, als den etwas betagten IGEL 1/1; leider ist der Wyse Sx0 sowas von zickig - hatte ich mittlerweile schon vergessen. Hier sei wieder <http://parkytowers.me.uk> erwähnt. M*st. Fast wäre mir der Blog-server samt Inhalt verloren gegangen (backup? was ist ein backup ;-))

Nun denn, schwierig ist/war eher alles wieder zum Laufen zu bringen, da der Wyse Sx0 sich weigert von CF-Karte zu starten, obwohl der Steckplatz vorhanden ist. Da ist wohl der CS_5536 Schuld; beim Starten wird die IDE einfach abgeschaltet (?). Und ich habe den Fehler gemacht die original Installation (zwekcs clonen) zu verwenden und zu vergessen, dass puppylinux in der Version 4.1.2 etwas anders bei Reparaturstarts reagiert.

Egal, nach 2 Tagen Try&Error ist wieder alles da (Liste der pets für später mal):
+ Puppylinux 4.1.2r3
+ Hiawatha 8.3 mit ReverseProxy, SSL (cmake 2.8.x)
+ Instiki 0.9 samt ruby 1.8.7
+ Perl 5.8.8 gesamtpaket
+ Openssh 1.x (client+server; /var/empty/..)
+ ddclient (/var/cache/.. )
+ Startup/Xprompt mit sleep xx, killall X
+ rc.local (mit obigen Startanweisungen)

Ach ja, und die Zuodnung beim DMZ nicht vergessen (da andere Netzwerk-ID).
