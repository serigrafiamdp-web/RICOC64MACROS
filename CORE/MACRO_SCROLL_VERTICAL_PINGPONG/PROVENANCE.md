# Provenance

La macro proviene del motor precursor **MOTOR CON SID VICIOUS ok**.

Routines relacionadas en la fuente original:

- `RenderizarBinarios()`
- `CambiarBufferPantalla()`
- `PrepararBufferArriba()`
- `PrepararBufferAbajo()`
- `DesplazarArriba()`
- `DesplazarAbajo()`

Datos confirmados:

- `char_data : incbin("char.bin",$C500)`;
- `char.bin` representa 2400 bytes = 40 × 60 filas;
- filas reales seleccionadas mediante `src_idx < 60`;
- Screen A `$0400-$07E7`;
- Screen B `$3000-$33E7`;
- cada preparación copia 24 filas del buffer activo y agrega una nueva fila en el buffer inactivo;
- el flip de pantalla cambia `$D018`;
- dirección e índices se mantienen separados del contenido real, permitiendo espacios de entrada/salida.

La versión original estaba acoplada a otras funciones del motor. Esta carpeta no contiene todavía una extracción portable del código: documenta el comportamiento probado que vamos a aislar.
