# Principio Abierto/Cerrado (OCP)

## Aplicación en el Sistema de Turnos Médicos

El Principio Abierto/Cerrado (OCP) establece que las entidades de software (clases, módulos, funciones, etc.) deben estar abiertas a la extensión, pero cerradas a la modificación. Esto significa que el comportamiento de un módulo puede extenderse sin alterar su código fuente original.

En el diseño del sistema de turnos médicos, el OCP se aplica en la gestión de la disponibilidad de los doctores mediante el patrón Strategy. Esto permite añadir nuevas reglas de disponibilidad sin modificar la clase `Doctor`.

### Estrategia de Disponibilidad para Doctores

Para manejar las distintas formas en que los doctores o recursos pueden tener disponibilidad (ej. médico general, quirófano, consulta externa), se introduce la interfaz `EstrategiaDisponibilidad`.

*   **Abierto a la extensión:** Se pueden añadir nuevas estrategias de disponibilidad (ej. `DisponibilidadMedicoGeneral`, `DisponibilidadQuirofano`, `DisponibilidadEmergencias`) simplemente creando nuevas clases que implementen la interfaz `EstrategiaDisponibilidad`. Cada nueva clase encapsulará la lógica específica para calcular las franjas horarias disponibles.
*   **Cerrado a la modificación:** La clase `Doctor` (que es el contexto) no necesita ser modificada cada vez que se introduce una nueva forma de calcular la disponibilidad. Su lógica para `consultarDisponibilidad()` se delega a la implementación actual de `EstrategiaDisponibilidad` a través de polimorfismo. El método `setEstrategia()` permite cambiar dinámicamente la estrategia.

### Beneficios de aplicar OCP

La aplicación del OCP en la gestión de la disponibilidad ofrece varios beneficios clave:

*   **Flexibilidad:** Permite al sistema adaptarse fácilmente a nuevas políticas de horarios, tipos de consulta o recursos (como quirófanos) sin alterar el código central de la gestión de doctores.
*   **Mantenibilidad:** Reduce el riesgo de introducir errores en el código existente al añadir nuevas funcionalidades, ya que las modificaciones se limitan a la creación de nuevas implementaciones de la interfaz.
*   **Escalabilidad:** El sistema puede crecer para soportar una mayor complejidad en la gestión de horarios y recursos médicos de manera controlada y organizada.

Este enfoque cumple con el requisito no funcional RNF3: "Posibilidad de extensión", asegurando que el sistema pueda evolucionar sin fricciones.