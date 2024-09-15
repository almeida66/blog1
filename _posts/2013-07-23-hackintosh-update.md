---
tags: hackintosh
---
Nachdem nun auch ein [ThinkPad T41](http://thinkwiki.de/T41) dazu gekommen ist und die Hardware-Kompatibilitaet viel besser ist, als die des R40, wurde wie folgt jeweils die Version 10.4.x aktualisiert.

Wichtig hierbei ist es den modifizierten Kernel immer beizubehalten. Immer!

Hierzu oeffnet man einen Terminal und mittels sudo -s wird man root. Dann folgt das Kopieren der wichtigen Dateien:
```
cp /mach_kernel /mach_kernel_old
cp -R /system/library/coreservices/loginwindow.app /
cp -R /system/library/extensions/AppleSMBIOS.kext /
cp -R /system/library/extensions/AppleACPIplatform.kext /
cp -R /system/library/extensions/AppleAPIC.kext /
cp -R /system/library/extensions/IOATAFamily.kext /
cp -R /system/library/extensions/system.kext /
```
Das Unterverzeichnis ist natuerlich frei waehlbar; bei der Gelegenheit wird Disk-Utility gestartet.

So, nun bei apple die zug. Updates, wie z.B. 10.4.9, 10.4.10, 10.4.11 runterladen. Immer nur ein Versionssprung installieren UND nicht neu starten.

Es folgt die Wiederherstellung der Dateien mit:
```
cp /mach_kernel_old /mach_kernel
cp -R /loginwindow.app /system/library/coreservices/
cp -R /AppleSMBIOS.kext /system/library/extensions/
cp -R /AppleACPIplatform.kext /system/library/extensions/
cp -R /AppleAPIC.kext /system/library/extensions/
cp -R /IOATAFamily.kext /system/library/extensions/
cp -R /system.kext /system/library/extensions/
rm -rf /system/library/extensions.*
```
Danach mittels Disk-Utility die Rechte prüfen und korrigieren lassen. Egal was das System von sich gibt. Neustart!

Der Neustart sollte erfolgreich sein; moeglich dass je nach Hardware ein zweiter Neustart erforderlich ist, bis alle Treiber angesprochen werden.

Das Ganze wird nun bis zum letzten Update wiederholt. Man kann dann auch die ueblichen Software-Updates installieren (solange der Kernel nicht betroffen ist).
