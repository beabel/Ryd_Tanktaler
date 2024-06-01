# Ryd_Tanktaler

https://fcc.report/FCC-ID/APV-3030GBT/2398777.pdf

https://www.icetrack.online/wiki/hardware/calamp

neue SIM sollte Pin entfernt sein!!
bei Traccar die ESN Nummer als Kennung nutzen.
(welche auf dem Sticker unter dem Tanktaler Sticker ist.)

SMS an Box:
APN -->           !RP,2306,0,xxx_APN_xxx
APN username -->  !RP,2314,0,xxx_username_xxx
APN password -->  !RP,2315,0,xxx_password_xxx

Server -->        !RP,2319,0,demo3.traccar.org
Server -->        !RP,2319,1,demo3.traccar.org
Port -->          !RP,769,0,5082
speichern -->     !RP,1024,35,255,1
Neustart -->      !R3,70,0


--------- Specials, welche nicht benötigt werden, jedoch Infos geben
!R4 <-- empfange Protokoll als SMS
!VV <-- versuche Car auslesen
!R0 <-- APN + GPS Info
!RP,1285,0,xxx_PIN_xxx <-- UNGETESTET SIM PIN setzen

---- ACHTUNG sollte nicht geändert werden ----
     !R0 IMEI <-- nutze IMEI statt ESN
--------------------
Infos zu acc's:
acc21: gefahrene Meter (aktueller Trip)
acc22: gefahrene Sekunden (aktueller Trip)
acc27: Batterie Spannung * 1000 (Auto)
acc30: Akku Spannung * 1000 (interner AKKU)
---------------------
APN Daten
Vodafone (user + pw nicht benötigt): !RP,2306,0,web.vodafone.de
---------------------
um aktuell eingestellte dinge abzufragen das Komma nach RP gegen ? tauschen und Wert weglassen z.Bsp.:
!RP?2306,0
