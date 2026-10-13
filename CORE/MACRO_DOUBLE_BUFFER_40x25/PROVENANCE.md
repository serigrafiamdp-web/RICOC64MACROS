# Provenance

Fuente: `MOTOR CON SID VICIOUS ok.txt`.

Rutina original: `CambiarBufferPantalla()`.

## Mapa original

| Estado | Screen | Charset real | D018 real | Charset máscara | D018 máscara |
|---|---:|---:|---:|---:|---:|
| A | $0400 | $2000 | $18 | $2800 | $1A |
| B | $3000 | $2000 | $C8 | $2800 | $CA |

Los valores dependen de la VIC bank original y deben recalcularse al portar.

## Patrón reutilizable

1. el buffer visible queda estable;
2. la CPU prepara el buffer inactivo;
3. se hace un flip corto;
4. se prepara inmediatamente el siguiente estado fuera de vista.

En el motor, `PrepararBufferArriba()` y `PrepararBufferAbajo()` construyen el próximo estado; `DesplazarArriba()` y `DesplazarAbajo()` realizan el flip cuando ese estado ya está listo.

La técnica sobrevivió en la evolución hacia RicOS, por eso pertenece a CORE.
