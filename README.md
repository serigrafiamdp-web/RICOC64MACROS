# RICO C64 MACROS

Biblioteca modular de rutinas y efectos Commodore 64 aislados de proyectos reales de RICO.

Objetivo: convertir soluciones que ya funcionaron en motores, demos y tests en componentes reutilizables, documentados y fáciles de integrar en proyectos nuevos sin tocar ni arriesgar los masters originales.

## Regla principal

Los proyectos fuente quedan intactos. Las rutinas se extraen, documentan y prueban aquí de forma independiente.

## Estados

- **READY**: aislada y probada como módulo reutilizable.
- **LEGACY_PASS**: funcionó en su proyecto de origen, todavía falta aislarla completamente.
- **COMPOSITE**: efecto construido combinando varias macros.
- **EXPERIMENTAL**: parcial, incompleta o pendiente de validación.
- **REFERENCE**: documentación útil, no necesariamente código portable todavía.

## Familias

- `CORE/` — scroll, buffers, streaming, charset.
- `COLOR_FX/` — degradados, radial, blink, paletas, mapas de color.
- `SID/` — player, rampas, sincronía, dual SID, audio procedural.
- `TIMING/` — PAL/NTSC, reloj lógico, correcciones fraccionales.
- `CONTROL/` — hotkeys, restart, salida limpia, secuenciación.
- `LEGACY/` — soluciones que funcionaron y luego fueron reemplazadas.
- `EXPERIMENTAL/` — prototipos útiles aún no consolidados.

## Contrato de cada macro

Cuando una rutina quede aislada deberá documentar:

- propósito;
- `INIT`;
- `TICK`;
- `RESET/OFF`;
- parámetros de configuración;
- RAM/ZP utilizadas;
- registros destruidos;
- dependencias;
- compatibilidad PAL/NTSC;
- origen y prueba PASS;
- limitaciones conocidas.

Ver `MACRO_STANDARD.md` y `MACRO_CATALOG.md`.

## Primer origen documentado

El primer motor que estamos desarmando es **MOTOR CON SID VICIOUS ok**, precursor directo de RicOS / Vicious Circles.

De allí salen, entre otras cosas, el scroll vertical PETSCII ping-pong, doble buffer, row streaming, animación de charset, máscara superior por raster, sincronía scroll/SID, turbo fraccional y modos de color legacy.
