# Contract draft

## INIT

La versión portable debe configurar:

- VIC bank;
- Screen A;
- Screen B;
- charset real;
- charset máscara opcional;
- buffer inicial.

## FLIP

`FlipScreen()` debe:

1. conmutar `screen_active`;
2. elegir el screen pointer;
3. conservar el charset activo;
4. escribir `$D018` una sola vez en un momento seguro del frame.

## RESET

Debe volver al buffer inicial y dejar `$D018` coherente.

## Outputs

- buffer visible;
- buffer inactivo;
- valor actual de `$D018`.

## Clobbers originales

A y flags.

## Dependencias

No necesita copiar Screen RAM. Eso se separa en `MACRO_ROW_STREAM_UP_DOWN`.

Puede cooperar con `MACRO_TOP_MASK_RASTER`.

## PASS requerido antes de READY

- patrón distinto en A y B;
- alternancia estable;
- sin tearing visible;
- prueba con charset real y máscara;
- validación PAL/NTSC.
