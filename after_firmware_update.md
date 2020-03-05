# Operazioni  post firmware update

## Operazioni da effettuare post upgrade firmware

### Importante

M502 ; factory reset

M500 ; save eeprom

M501 ; restore settings

### Da pannello LCD:

 1. CONFIGURATION
 2. DELTA CALIBRATION
 3. AUTO CALIBRATION
 4. STORE SETTINGS



### Calibrare ZOffset
effettuare operazioni per calibrare lo zoffset del probe rispetto al piatto.

### Creare Mesh UBL

 - **G28** ; home xyz
 - **G29 P1** ; automatically build your first mesh
 - **G29 T** ; visualizza valori mesh (topology map)
 - **G29  P3** ; riempie i valori vuoti (esterni alla circonferenza del piatto)-  **Fill Unpopulated** regions of the mesh with a fixed    value
 - **G29 S** ; salva valori 
 - **G29 F10.0**
 - **G29A** ; attiva UBL
 - **M500**; save EEPROM

### Se si vuole testare la mesh, si può usare il comando G26

G26 B50 H240 F1.75 L0.2 S0.4 P10

#### ATTENZIONE: Scenderà molto veloce fino alla Z0

## Test effettuato usando il file preso su [Thingiverse](https://www.thingiverse.com/thing:3491036) al 161% di zoom

## Risultato finale

![Bed Leveling test](https://github.com/lele344/Predator/blob/master/immagini/bed_leveling.png)
