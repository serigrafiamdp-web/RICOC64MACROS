# Contract draft

## INIT

Debe recibir/configurar:

- base del mapa;
- ancho del mapa (primera versión: 40);
- cantidad de filas;
- Screen A;
- Screen B;
- charset/VIC bank;
- fila inicial;
- límites de cambio de dirección;
- velocidad/paso inicial.

## TICK

Un tick debe:

1. actualizar fine scroll;
2. detectar cruce de fila;
3. conmutar al buffer preparado cuando corresponda;
4. actualizar índice lógico;
5. preparar el siguiente buffer inactivo;
6. invertir dirección al alcanzar el límite.

## RESET

Debe dejar:

- fine scroll en estado conocido;
- Screen A/B coherentes;
- índice/dirección reiniciados;
- ningún IRQ opcional activo.

## RAM/ZP original

La versión legacy usa punteros temporales y variables globales del motor. Antes de READY se documentarán exactamente y se hará configurable el uso de Zero Page.

## Compatibilidad

La lógica de scroll es candidata a PAL/NTSC, pero la velocidad temporal debe delegarse a TIMING. No marcar READY multisistema hasta probarla de forma aislada.
