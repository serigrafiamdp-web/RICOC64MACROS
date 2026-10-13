# MOTOR CON SID VICIOUS ok

Motor precursor usado antes de la construcción del RicOS final.

## Fuente analizada

Archivo recibido: `MOTOR CON SID VICIOUS ok.zip`.

Contiene una única fuente TRSE textual:

- `MOTOR CON SID VICIOUS ok.txt`
- 84003 bytes.

## Capacidades visibles en esta versión

- scroll vertical PETSCII ping-pong;
- mapa real de **40 × 60 filas** (`char.bin` = 2400 bytes);
- recorrido con zonas vacías de entrada/salida y cambio de dirección;
- Screen A `$0400` / Screen B `$3000`;
- doble buffer y flip mediante `$D018`;
- charset real en `$2000`;
- charset vacío/máscara en `$2800`;
- música Vicios en `$8C00`;
- mapa PETSCII en `$C500`;
- row streaming arriba/abajo;
- animación de glyphs en cuatro direcciones;
- modos de color: degradado, blink global, blanco, blink selectivo y COLOR.BIN;
- scroll enlazable al SID;
- rampa de SID;
- turbo final fraccional;
- corte del player antes del loop;
- release tail;
- sincronización del cierre visual con el final musical.

## Nota sobre “120 filas”

El recurso fuente contiene 60 filas reales. El efecto recorre ese mapa de ida y vuelta, por lo que un ciclo completo representa aproximadamente 120 filas de desplazamiento útil, además de la entrada/salida vacía. En las macros se documentará siempre por separado:

- tamaño del mapa real;
- distancia/recorrido del efecto.
