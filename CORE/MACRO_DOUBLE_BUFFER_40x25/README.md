# MACRO_DOUBLE_BUFFER_40x25

**STATUS:** LEGACY_PASS  
**ORIGIN:** MOTOR CON SID VICIOUS ok  
**TARGET:** READY

## Qué resuelve

Mantener dos pantallas de 40×25 caracteres:

- Screen A: `$0400-$07E7`
- Screen B: `$3000-$33E7`

El VIC-II muestra una pantalla completa mientras la CPU prepara la otra. Cuando el buffer inactivo está listo, el cambio visible se reduce a actualizar `$D018`.

Valores originales:

- A + charset real `$2000`: `$D018=$18`
- B + charset real `$2000`: `$D018=$C8`
- A + charset máscara `$2800`: `$D018=$1A`
- B + charset máscara `$2800`: `$D018=$CA`

## Separación

Esta macro administra qué buffer está visible. El copiado/desplazamiento de filas pertenece a `MACRO_ROW_STREAM_UP_DOWN`.

La regla importante del motor original era: **nunca modificar la pantalla que el VIC está mostrando**.

## Estado

Funcionó en el motor precursor y la arquitectura sobrevivió en RicOS.

Todavía no es READY porque la implementación original usa direcciones y valores VIC hardcodeados. Falta aislarla y hacer un test mínimo independiente.
