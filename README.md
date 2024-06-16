# Ryd Tanktaler weiter nutzen mit eigenen Traccar Server

## Vorbereitungen:
1. **Traccar Server einrichten:**
   - Port `5082` für Daten vom Calamp durchleiten.
   - Port `8082` durchleiten, wenn WebAnsicht auch von außen gewünscht wird.
   
2. **DynDNS einrichten:**
   - DynDNS auf dem Router einrichten.
   - Beispiel bei einer FritzBox: `il0hhfbacskhfmax.myfritz.net`

3. **Neues Gerät auf dem Traccar Server einrichten:**
   - Als Kennung die `ESN` verwenden, die sich unter dem Tanktaler/Ryd Kleber befindet.

## Stecker einrichten:
1. **Stecker vorsichtig öffnen:**
   - Mit einem Schraubendreher leicht an den Seiten drehen, um die Seiten auseinander zu schieben.

2. **Alte SIM entfernen:**
   - Verwende eine Nadel, um die Karte herauszuschieben.

3. **SIM Sperre entfernen:**
   - Mit einem Handy die SIM Sperre auf der neuen Karte entfernen.
   - Hinweis: Es wird eine große, originale SIM benötigt (neue Phones haben meist kleinere SIMs).

4. **Neue SIM einlegen:**
   - Die neue SIM in den Stecker einlegen.

5. **Einrichtungs-SMS senden:**
   - Am besten mit angeschalteter Zündung die Einrichtungs-SMS absenden.
   - Bei ausreichend Guthaben sollte immer ein "OK" zurückkommen.

### Beispiel für eine komplette SMS-Befehlsabfolge:
(APN Netzclub: `pinternet.interkom.de`, Traccar Server: `demo3.traccar.org`)

Beispiel für eine komplette SMS Befehls abfolge (pinternet.interkom.de == APN Netzclub / demo3.traccar.org == Traccar Server):
```
!RP,2306,0,!RP,2306,0,pinternet.interkom.de
!RP,2319,0,demo3.traccar.org
!RP,769,0,5082
!RP,1024,35,255,1
!R3,70,0
```
APN  
Server  
Port  
speichern  
Neustart  

## Weitere Informationen:
https://fcc.report/FCC-ID/APV-3030GBT/2398777.pdf

https://www.icetrack.online/wiki/hardware/calamp

- neue SIM sollte Pin entfernt sein!!
- bei Traccar / Ruhavik die ESN Nummer als Kennung nutzen.
- (welche auf dem Sticker unter dem Tanktaler Sticker ist.)

SMS an Box:
> [!NOTE]
> APN
> -     !RP,2306,0,xxx_APN_xxx
> APN username (meist nicht benötigt)
> -     !RP,2314,0,xxx_username_xxx
> APN password (meist nicht benötigt)  
> -     !RP,2315,0,xxx_password_xxx

> [!TIP]
> SERVER
  > -      !RP,2319,0,demo3.traccar.org
  > -      !RP,2319,1,demo3.traccar.org
> Port (Traccar = 5082 / Ruhavik = 21007)
  > -      !RP,769,0,5082

> [!TIP]
> speichern
  > -      !RP,1024,35,255,1
> Neustart
  > -      !R3,70,0


--------- Specials, welche nicht benötigt werden, jedoch Infos geben
- !R4 <-- empfange Protokoll als SMS
- !VV <-- versuche Car auslesen
- !R0 <-- APN + GPS Info
- !RP,1285,0,xxx_PIN_xxx <-- UNGETESTET SIM PIN setzen

---- ACHTUNG sollte nicht geändert werden ----
> [!CAUTION]
> ACHTUNG sollte nicht geändert werden (nutze IMEI statt ESN)
> -      !R0 IMEI
--------------------
Infos zu acc's:
- acc21: gefahrene Meter (aktueller Trip)
- acc22: gefahrene Sekunden (aktueller Trip)
- acc27: Batterie Spannung * 1000 (Auto)
- acc30: Akku Spannung * 1000 (interner AKKU)
---------------------
APN Daten
- Vodafone (user + pw nicht benötigt): !RP,2306,0,web.vodafone.de
- Netzclub (user + pw nicht benötigt): !RP,2306,0,pinternet.interkom.de
- O2 (user + pw nicht benötigt): !RP,2306,0,internet
---------------------
- um aktuell eingestellte dinge abzufragen das Komma nach RP gegen ? tauschen und Wert weglassen z.Bsp.:
- !RP?2306,0
