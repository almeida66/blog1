---
tags: OpenWrt
---
## RasPi als Wetterserver II
Und es geht doch mit **OpenWrt**; man muss halt das Kleingedruckte lesen. Allerdings ist der wifi-chip des Raspi zero w nicht stabil, habs doch wieder mit einem wifi-usb-Adapter umgesetzt.

Die Huerde ist z.T. die Installation der python3-Dateien. u.a. :
- python3-light
- python3-django
- python3-pip
- python3-pillow

es folgen:
```
python3 -m pip install cheetah3
python3 -m pip install pyusb (ggf. pyserial, je nach Wetterstation)
python3 -m pip install configobj
```
Dann via wget die aktuelle weewx-x.x.x.tar.gz laden und mittels `tar -zxvf` extrahieren. Es folgt die Installation mit `python3 setup.py install`.

Zuletzt diverse Anpassungen in der Config-Datei; es macht Sinn den *Debug-modus* auf **1** zu stellen. 
