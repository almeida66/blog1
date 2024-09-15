Puh, das backup ist nun vollbracht; sind im Laufe der Zeit schon noch der eine oder andere blog-Eintrag dazugekommen.

Ich habe dazu eine einfachst Lösung für die Verwendung innerhalb von github gesucht, sollte allerdings sowas wie ein blog-Aufbau haben.
Bin dann beim user [chadbaldwin](https://chadbaldwin.net/2021/03/14/how-to-build-a-sql-blog.html) fuendig geworden.

D.h. (z.B.) man legt eine **subdomain** im bereits bestehendem github-account an und kopiert dann das [template](https://github.com/chadbaldwin/simple-blog-bootstrap). Die Konfigurationsdatei _config.yml wird ergänzt und ggf. index.md befüllt. 

Unter **_posts** werden die blog-Dateien in der Form *Jahr-Monat-Tag-Titel.md* angegeben; der Inhalt wird in sog. *markdown* Syntax formatiert.
Das template ist nicht ganz vollständig, z.B. habe ich verzweifelt nach einer Begrenzung der blog-Zeilen auf der Frontseite gesucht. Nun ja, es fehlen im template unter **_layouts** die home- und default-Dateien. Dort wird bereits ein *home_post_limit* mitgegeben. Diese einfach von obigem repository kopieren. 
Die andere Methode wäre *jekyll-paginate* zu verwenden, allerdings habe ich das nur fürs sog. *blog-archive* zum laufen gebracht.

Kleiner Hinweis noch: durch die spezifische Verwendung einer subdomain, sollte man die html-Pfade in archive.md ergänzen und zwar stur mittels "a href="**/subdomain**{{ post.url }}...". Gleiches gilt für die Navigation-Vorgabeseite unter **_includes**. Das Ganze innerhalb der _config.yml zu konfigurieren hat nicht geklappt.

Hierbei noch das *jekyll-plugin* integrieren; scheinbar hat github dies zwischenzeitlich umstrukturiert; das template hat vor 2024 ohne explizite Zuweisung im Hintergrund (Actions) die Seiten veroeffentlicht.

>[!NOTE]
>Es ist zudem ein Unterschied ob man lokal via git arbeitet oder direkt auf github. 
