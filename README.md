# Marlin bugfix_2.0.x BTT SKR 1.4 TURBO for Anycubic Predator delta

* SKR 1.4 TURBO (LPC1769)
* BTT TMC2209 con il PIN DIAG tagliato
* TFT 35 V3
* BTT FILAMENT SENSOR


## Rimappatura porte:

```
ZMAX = PWRDET (PIN1_00)
YMAX = E1DET (PIN1_25)
XMAX = E0DET (PIN1_26)
FAN HOTEND = HE1 (PIN2_04)  (si accende se l'hotend raggiunge i 50 gradi)
FAN MATERIAL = FAN0 (PIN2_03)
PROBE PORT = probe port (P0_10)
```

---
Configuation.h
#define Z_MIN_PROBE_USES_Z_MIN_ENDSTOP_PIN

e assegnare:
#define Z_MIN_PROBE_PIN P0_10 (Probe port)



## UNIFIED BED LEVELING
Se la EEPROM non è stata inizializzata, ti dirà di emettere la sequenza M502, M500, M501.
```
G28      ; home
G29 P1   ; sondare automaticamente il letto
G29 P3   ; riempimento intelligente dei punti mesh mancanti
M420 V   ; Stampa una mappa della mesh
G26      ; stampa motivo per testare accuratezza della mesh
G29 S[n] ; salverà la mesh in EEPROM.
```

## CONNESSIONI:

Sono presenti 4 connessioni motori. X, Y, Z ed E.

Esistono 3 connessioni ottiche per finecorsa. X, Y e Z (impostate sui MAX)

- connessione sonda.
- una connessione del sensore del filamento.
- un connettore della ventola per il raffreddamento della scheda.
- un connettore della ventola per i 2 set di ventole montati sull'effettore.
- un connettore termistore hotend.
- un connettore del termistore del letto riscaldato.
- ci sono fili scoperti per il letto riscaldato, hotend e alimentazione nei cavi.



## CABLAGGIO (da verificare perchè vado a memoria)

FINECORSA GEEETECH OCPO OPTICAL SENSOR
SENSORI        PIN S - +
TRIGORILLA PRO PIN + - s
SKR 1.4 TURBO  PIN S - +

Se si vogliono usare i cavi originali, bisognerà invertire i due pin estremi.
Se si vogliono tirare dei cavi nuovi, rispettare l'ordine.

Le uniche connessioni che richiedono modifiche importanti sono i connettori della ventola. Il connettore trigorilla aveva entrambi i set di ventole funzionanti da un connettore, ma la SKR 1.4 non ha questa capacità. Tutte e tre le ventole sono collegate tra loro usando il positivo.

I fili sono i seguenti:

Rosso - Fan 2 (Hotend fan) terra
Blu - Fan 0 (parte ventole di raffreddamento) a terra
Giallo: positivi per tutti e 3 i fan collegati insieme.

## MODIFICHE EFFETTUATE per aver tagliato il PIN DIAG 

Disabilitati i diag pin su pins_BTT_SKR_V1_4.h (la turbo usa la stessa tabella infatti ha un include nel file del turbo) 
```
//
// TMC StallGuard DIAG pins
//
//#define X_DIAG_PIN         P1_26   // X-STOP
//#define Y_DIAG_PIN         P1_25   // Y-STOP
//#define Z_DIAG_PIN         P1_00   // Z-STOP
//#define E0_DIAG_PIN        P1_29   // E0DET
//#define E1_DIAG_PIN        P1_25   // E1DET
#define Z_MIN_PIN     P1_27
#define X_MAX_PIN     P1_26
#define Y_MAX_PIN     P1_25
#define Z_MAX_PIN     P1_00
//
```

## Aggiunta guida per operazioni post firmware upgrade


[Vai alla guida](https://github.com/lele344/Predator/blob/master/after_firmware_update.md)

