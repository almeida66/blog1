Ja, das geht ganz gut, sogar mit Netzwerkkarten. Nicht alle, aber z.B. die Intel pro/100, einige Realtek 8139 oder von 3com bieten einen plcc32 Stecksockel; die ganz alten haben noch einen DIL32-Stecksockel.

Auch hier findet flashrom Anwendung, oder halt die Hersteller eigenen Utils à lá fboot.exe (Intel). Leider ist hier zu beachten, dass die Karten nur 5V ROM's aufnehmen.

Die Wyse haben (warum auch immer) einen 3,6V Baustein. Jedenfalls benötigt man keine teure Hardware. Der Tipp kommt übrigens von [hier](http://sandeen.net/fwfix/).

Beim einem ganz alten Board (Axus TC320), der sehr ähnlich dem Optoma ST320E oder Futro B100 ist, war ein DIP32 ROM eingebaut. Mangels geeigneter Netzwerkkarte mit 256k, musste ein alter PC herhalten. Diesmal mit [uniflash](http://web.archive.org/web/20080101141938/http://www.uniflash.org/); dieses Tool arbeitet hervorragend mit Boards, obwohl mittels der Option -PCIROM ggf. auch Netzwerkkarten in Frage kommen.

Jedenfalls konnte ich mit dem Fremd-BIOS obiges Gerät zum Leben erwecken. Es tut gerade hier seine Dienste mit sparsamen 9W.
