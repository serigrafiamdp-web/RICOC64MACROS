# Catálogo inicial de macros

Este catálogo reúne capacidades resueltas durante la evolución del motor precursor y RicOS / Vicious Circles. Todavía no significa que todas estén aisladas.

## CORE

| Macro | Estado | Origen | Descripción |
|---|---|---|---|
| `MACRO_SCROLL_VERTICAL_PINGPONG` | LEGACY_PASS | MOTOR CON SID VICIOUS | Scroll vertical PETSCII suave, bidireccional, sobre mapa 40×60; recorrido ida/vuelta. |
| `MACRO_DOUBLE_BUFFER_40x25` | LEGACY_PASS | MOTOR CON SID VICIOUS | Screen A $0400 / Screen B $3000, construcción del frame siguiente fuera de pantalla y flip por $D018. |
| `MACRO_ROW_STREAM_UP_DOWN` | LEGACY_PASS | MOTOR CON SID VICIOUS | Inyección de nueva fila arriba o abajo mientras se desplaza la ventana visible. |
| `MACRO_TOP_MASK_RASTER` | LEGACY_PASS | MOTOR CON SID VICIOUS | Recorte superior alternando charset vacío/real por raster, sin modificar Screen RAM. |
| `MACRO_CHARSET_ANIM_4WAY` | LEGACY_PASS | MOTOR CON SID VICIOUS | Rotación de bits por glyph: izquierda, derecha, arriba y abajo según listas de screen codes. |
| `MACRO_CHARSET_BACKUP_RESTORE` | REFERENCE | RicOS final | Guarda y restaura glyphs originales para replay/reinicio limpio. |
| `MACRO_STAGE13_GHOST_SCROLL` | COMPOSITE | RicOS final | Pantalla PETSCII centrada visualmente estática mientras el motor mantiene timing interno. |

## COLOR_FX

| Macro | Estado | Origen | Descripción |
|---|---|---|---|
| `MACRO_BLINK_GLOBAL` | LEGACY_PASS | MOTOR CON SID VICIOUS | Blink de Color RAM con secuencia configurable. |
| `MACRO_BLINK_SELECTIVE_CODES` | LEGACY_PASS | MOTOR CON SID VICIOUS | Screen code → LUT de 256 entradas → color; sólo parpadean los códigos elegidos. |
| `MACRO_COLOR_MAP_BIN` | LEGACY_PASS | MOTOR CON SID VICIOUS | Color RAM alimentada por mapa externo que acompaña el row streaming. |
| `MACRO_DEGRADE_LINEAR` | REFERENCE | RicOS final | Bandas horizontales/degradado lineal. |
| `MACRO_DEGRADE_VERTICAL` | REFERENCE | RicOS final | Bandas verticales configurables. |
| `MACRO_DEGRADE_VERTICAL_SCROLL` | REFERENCE | RicOS final | Variación animada/desplazada del degradado vertical. |
| `MACRO_DEGRADE_RADIAL` | REFERENCE | RicOS final | Color radial con centro/ancla actualizable. |
| `MACRO_DEGRADE_PERIODIC` | REFERENCE | RicOS final | Patrón periódico/cruzado configurable. |
| `MACRO_ROTATING_LINES` | REFERENCE | RicOS final | Efecto basado en mapas de líneas rotatorias precomputados. |
| `MACRO_HORIZONTAL_BW` | REFERENCE | RicOS final | Barrido horizontal blanco/negro usado como efecto de stage. |
| `MACRO_PALETTE_0_9` | REFERENCE | RicOS final | Selección y ciclo de diez paletas AYAHUASCA. |
| `MACRO_PALETTE_DEFERRED_WORKER` | REFERENCE | RicOS final | Remapeo de color distribuido en pequeños chunks para no bloquear un frame. |

## SID

| Macro | Estado | Origen | Descripción |
|---|---|---|---|
| `MACRO_SCROLL_SID_SYNC` | LEGACY_PASS | MOTOR CON SID VICIOUS | La cadencia del scroll sigue la frecuencia efectiva del player SID. |
| `MACRO_SID_RATE_RAMP` | LEGACY_PASS | MOTOR CON SID VICIOUS | Rampa progresiva de frecuencia de llamadas PLAY. |
| `MACRO_SID_TRIGGER_ON_CONTENT` | LEGACY_PASS | MOTOR CON SID VICIOUS | Dispara la rampa musical cuando entra el primer contenido real. |
| `MACRO_SID_TURBO_FRACTIONAL` | LEGACY_PASS | MOTOR CON SID VICIOUS | Entre SID 40–50 Hz aumenta suavemente los píxeles/frame mediante acumulador fraccional. |
| `MACRO_SID_CUT_BEFORE_LOOP` | LEGACY_PASS | MOTOR CON SID VICIOUS | Cuenta llamadas reales a PLAY y corta antes del retrigger del loop. |
| `MACRO_SID_RELEASE_TAIL` | LEGACY_PASS | MOTOR CON SID VICIOUS | Detiene PLAY pero deja una cola temporal para el release natural del SID. |
| `MACRO_DUAL_SID_DETECT` | REFERENCE | RicOS final | Detección de segundo SID / perfiles usados por SYSINFO64. |
| `MACRO_DUAL_SID_WRITE_THROUGH` | REFERENCE | RicOS final | Duplica comandos del SID principal hacia un segundo SID confirmado. |
| `MACRO_SID_OCEAN` | REFERENCE | RicOS final | Motor procedural de olas usando SID, fases, noise, filtros y envelopes. |

## TIMING

| Macro | Estado | Origen | Descripción |
|---|---|---|---|
| `MACRO_WAIT_VBLANK` | LEGACY_PASS | MOTOR CON SID VICIOUS | Sincronización simple con raster antes del trabajo gráfico. |
| `MACRO_VIDEO_STANDARD_DETECT` | REFERENCE | RicOS final | Diferencia PAL-B, Drean PAL-N, NTSC y NTSC OLD mediante medición temporal. |
| `MACRO_MULTISTANDARD_LOGICAL_CLOCK` | REFERENCE | RicOS final | Reloj lógico independiente del frame rate físico. |
| `MACRO_FRACTIONAL_PIXEL_CORRECTION` | REFERENCE | RicOS final | Correcciones de velocidad del orden de fracciones de píxel usando acumuladores/cadencias. |
| `MACRO_NTSC_STAGE5_UNIFORM` | REFERENCE | RicOS final | Corrección específica de stage 5 para NTSC. |
| `MACRO_PALB_UNIFORM_CADENCE` | REFERENCE | RicOS final | Corrección de cadencia PAL-B / soporte relacionado con NTSC OLD. |

## CONTROL

| Macro | Estado | Origen | Descripción |
|---|---|---|---|
| `MACRO_STAGE_SEQUENCER` | REFERENCE | RicOS final | Secuenciador de stages que gobierna efectos, dirección y timing. |
| `MACRO_VISUAL_END_SYNC` | LEGACY_PASS | MOTOR CON SID VICIOUS | Arma el cierre visual una cantidad configurable de PLAY antes del final musical. |
| `MACRO_HOTKEY_MATRIX` | REFERENCE | RicOS final | Controles 0–9 y hotkeys de intro/demo/outro. |
| `MACRO_CLEAN_RESTART` | REFERENCE | RicOS final | Restablece estado visual/charset para replay sin reset físico. |
| `MACRO_RETURN_BASIC` | REFERENCE | RicOS final | Salida limpia restaurando estado necesario antes de BASIC. |
| `MACRO_OUTRO_LINE25_SCROLL` | REFERENCE | RicOS final | Scroller independiente de texto en línea 25. |

## EXPERIMENTAL / HISTÓRICAS

| Macro | Estado | Origen | Descripción |
|---|---|---|---|
| `MACRO_AYAH_LINEAR_MASK` | EXPERIMENTAL | RicOS source master | Helper/prototipo para optimización lineal de máscara. |
| `MACRO_OUTRO_VOICE1_3FX` | EXPERIMENTAL | RicOS source master | Variante experimental de tres efectos para Voice 1 del océano. |
| `MACRO_SCROLL_BONUS_VARIANTS` | EXPERIMENTAL | Tests RicOS | Familia de ajustes porcentuales/fraccionales usada durante calibración multisistema. |

## Prioridad de aislamiento

1. `MACRO_SCROLL_VERTICAL_PINGPONG`
2. `MACRO_DOUBLE_BUFFER_40x25`
3. `MACRO_ROW_STREAM_UP_DOWN`
4. `MACRO_TOP_MASK_RASTER`
5. `MACRO_CHARSET_ANIM_4WAY`
6. `MACRO_SCROLL_SID_SYNC`
7. `MACRO_SID_TURBO_FRACTIONAL`
8. `MACRO_BLINK_SELECTIVE_CODES`

El objetivo es promover cada candidata a **READY** sólo después de aislarla y probarla en un test mínimo.
