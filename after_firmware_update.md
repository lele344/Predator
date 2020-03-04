Operazioni da effettuare post upgrade firmware

M502 
M500
M501

Da pannello LCD
CONFIGURATION
  DELTA CALIBRATION
    AUTO CALIBRATION

quando finito 
    STORE SETTINGS

Calibrare ZOffset

Creare Mesh UBL

G28
G29 P1 - UBL mesh
G29 T - visualizza valori mesh
G29 P3 - riempie i valori vuoti (esterni alla circonferenza del piatto)
G29 S - salva valori
G29 F10.0
G29A - attiva UBL
M500

Se si vuole testare la mesh, si può usare il comando G26

G26 B50 H240 F1.75 L0.2 S0.4 P10

ATTENZIONE: Scenderà molto veloce fino alla Z0
