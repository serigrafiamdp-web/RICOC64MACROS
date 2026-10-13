# MACRO_SCROLL_VERTICAL_PINGPONG

**STATUS:** LEGACY_PASS  
**ORIGIN:** MOTOR CON SID VICIOUS ok  
**TARGET:** convertir a READY

## Qué resuelve

Scroll vertical suave de un mapa PETSCII mayor que la pantalla visible, con movimiento hacia arriba y hacia abajo y cambio automático de dirección.

La versión original usa:

- mapa: 40 × 60 filas reales;
- viewport: 40 × 25;
- Screen A: `$0400`;
- Screen B: `$3000`;
- fine scroll VIC-II;
- row streaming;
- recorrido ping-pong;
- zonas vacías antes/después del mapa.

## Qué NO forma parte obligatoria de esta macro

En el motor original estaba integrada con SID, turbo, color y animación de charset. La versión portable debe separar esas capacidades como dependencias opcionales.

## Dependencias candidatas

- `MACRO_DOUBLE_BUFFER_40x25`
- `MACRO_ROW_STREAM_UP_DOWN`

Opcionales:

- `MACRO_SCROLL_SID_SYNC`
- `MACRO_TOP_MASK_RASTER`
- `MACRO_CHARSET_ANIM_4WAY`
- macros de COLOR_FX.

## Próximo trabajo

1. aislar solamente scroll + buffer + row streaming;
2. reemplazar direcciones mágicas por configuración;
3. definir INIT/TICK/RESET;
4. probar mapa pequeño y mapa 40×60;
5. validar subida, bajada y cambio de dirección;
6. recién entonces promover a READY.
