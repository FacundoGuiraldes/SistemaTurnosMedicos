# Documentación de Uso de IA - Especialista OCP

## 🤖 Herramienta Utilizada
**[Cursor - Agent Mode]**

## 💬 Prompt Utilizado

```
Actúa como especialista en arquitectura de software. Identifica dos clases del Sistema de Turnos Médicos que violen el principio OCP y propón una refactorización usando el patrón Strategy.
```

## 📂 Archivos de contexto referenciados
* `anexos/introduccion.md`
* `diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw`
* `herramientas-agile/tarjetas-crc/04-tarjeta-crc-doctor.md`
* `herramientas-agile/tarjetas-crc/06-tarjeta-crc-agenda.md`
* `herramientas-agile/tarjetas-crc/05-tarjeta-crc-turno.md`

## 📤 Output obtenido (Fragmento representativo)
La IA propuso una refactorización con una interfaz `EstrategiaDisponibilidad`, estrategias concretas para distintos contextos médicos y una reorganización de `Doctor` y `Agenda` para delegar la definición y validación de disponibilidad sin modificar sus responsabilidades principales.

## 🛠️ Ajustes realizados
1. **Focalización en clases del dominio:** Se descartaron abstracciones genéricas que no aportaban al dominio y se aterrizó la solución a clases reales del sistema (`Doctor`, `Agenda` y `Turno`) identificadas en el boceto y las tarjetas CRC.
2. **Refuerzo de la justificación OCP:** Se explicitó que el principio impacta sobre dos clases principales: `Doctor`, que delega el cálculo de disponibilidad, y `Agenda`, que valida turnos contra una estrategia extensible.
3. **Corrección del diagrama UML:** Tras una revisión técnica, se corrigió una ambigüedad para explicitar que `Agenda` también posee una referencia a la estrategia, permitiendo que la validación sea independiente del tipo de recurso médico.