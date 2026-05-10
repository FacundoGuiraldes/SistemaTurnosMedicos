# Uso de Copilot Agent Mode - SRP

## Promp utilizado

```text
Leé los siguientes archivos del proyecto como contexto:

* anexos/introduccion.md
* diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw
* herramientas-agile/tarjetas-crc/

A partir de ese contexto, realizá lo siguiente:

1. Identificá al menos 3 clases principales del sistema que presenten múltiples responsabilidades (que no cumplan con el principio de Responsabilidad Única - SRP).

2. Para cada clase identificada:

   * Describí cuáles son sus responsabilidades actuales.
   * Explicá por qué esas responsabilidades están mezcladas.
   * Indicá qué problemas de mantenibilidad genera.

3. Proponé una refactorización aplicando SRP:

   * Separá las responsabilidades en nuevas clases.
   * Indicá el nombre de cada nueva clase.
   * Explicá qué responsabilidad tendría cada una.
```
---

## Archivos de contexto utilizados

* anexos/introduccion.md
* diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw
* herramientas-agile/tarjetas-crc/

---

## Output obtenido

Copilot identificó tres clases principales con múltiples responsabilidades: `Sistema`, `Paciente` y `Turno`.

Para cada una, explicó que concentraban distintas funciones, como lógica de negocio, manejo de datos y validaciones, lo cual generaba problemas de mantenibilidad, acoplamiento y dificultad de testeo.

Además, propuso una refactorización basada en separar responsabilidades en nuevas clases específicas, como `ValidadorTurnos`, `ServicioNotificaciones`, `DatosPaciente`, `GestorSolicitudTurnos`, `DatosTurno` y `GestorEstadoTurno`.

---

## Ajustes realizados al Output

Se simplificó el análisis generado por Copilot para adaptarlo a un nivel académico más claro y comprensible.

Se eliminaron detalles excesivamente técnicos y listas extensas de métodos, manteniendo únicamente las ideas principales necesarias para explicar la aplicación del principio SRP.

También se reorganizó la información para que coincida con la estructura solicitada en el archivo `01-srp.md`, asegurando coherencia entre el análisis, el diagrama UML y la justificación técnica.
