# Auditoría de IA - Especialista en LSP

* **Prompt utilizado:**
```text
Analiza las jerarquías de herencia propuestas para el Sistema de Turnos Médicos y verifica si se cumple el Principio de Sustitución de Liskov (LSP) para la clase Doctor. Propón una jerarquía simple y coherente con el dominio, indicando por qué una subclase puede sustituir a su superclase sin alterar el comportamiento esperado.
```
* **Archivos de contexto:** `anexos/introduccion.md`, `diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw`, `herramientas-agile/tarjetas-crc/04-tarjeta-crc-doctor.md`, `herramientas-agile/tarjetas-crc/06-tarjeta-crc-agenda.md`, `herramientas-agile/tarjetas-crc/05-tarjeta-crc-turno.md`.
* **Output obtenido:** Propuesta de una jerarquía con `Doctor` como clase abstracta y especialidades concretas (`Cardiologo`, `Pediatra` y `Traumatologo`), acompañada por una explicación sobre contrato de comportamiento, uso polimórfico de `verAgenda(): void` y condiciones para que las especialidades médicas puedan reutilizar la misma interfaz pública sin romper clientes existentes.
* **Ajustes críticos realizados:** Se alineó la documentación con el diagrama final agregando más de un subtipo concreto y explicitando el contrato esperado de `verAgenda(): void`. También se corrigió la descripción del resultado para eliminar referencias a Strategy que pertenecen al análisis de OCP y reforzar que el contexto usado incluye introducción, boceto inicial y tarjetas CRC relevantes.
