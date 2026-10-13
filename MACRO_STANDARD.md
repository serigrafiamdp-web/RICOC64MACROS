# Standard de macros

Una macro entra al catálogo antes de estar completamente aislada. El estado indica cuánto podemos confiar en ella.

## Estados

### READY
Módulo aislado, con contrato claro y prueba independiente PASS.

### LEGACY_PASS
La rutina funcionó en el motor/proyecto de origen, pero todavía depende de direcciones, variables o recursos de ese proyecto.

### COMPOSITE
Efecto de nivel superior formado por varias macros.

### EXPERIMENTAL
Rutina parcial, prueba histórica o solución que todavía necesita validación.

### REFERENCE
Capacidad confirmada en un proyecto final, identificada para extracción, pero aún no convertida en módulo.

## Ficha obligatoria

Cada macro aislada debe tener:

- **NAME**
- **STATUS**
- **ORIGIN**
- **PURPOSE**
- **INIT**
- **TICK**
- **RESET/OFF**
- **CONFIG**
- **INPUTS**
- **OUTPUTS**
- **RAM**
- **ZERO PAGE**
- **CLOBBERS**
- **DEPENDENCIES**
- **PAL/NTSC**
- **KNOWN LIMITATIONS**
- **PASS/FAIL LOG**

## Regla de portabilidad

Una macro no pasa a READY sólo porque funcionó dentro de RicOS o de un motor anterior.

Para READY debe poder integrarse en un test mínimo sin depender accidentalmente de:

- direcciones mágicas no declaradas;
- variables globales externas;
- orden de inicialización implícito;
- recursos que no estén listados;
- estado previo del VIC/SID/CIA;
- ROM mapping no documentado.

## Regla de memoria

Siempre documentar el mapa original y el mapa requerido por la versión portable. Una dirección usada en el proyecto original no se considera requisito salvo que la macro realmente lo necesite.
