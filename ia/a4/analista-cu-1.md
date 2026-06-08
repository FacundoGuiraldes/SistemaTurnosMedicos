# Bitácora de IA - Analista Funcional CU 1

### Archivos de Contexto Utilizados
* diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw
* diagramas/02-casos-de-uso/02-caso-uso-solicitar-turno.png
* diagramas/03-escenarios-casos-de-uso/03-solicitar-turno-escenario-01.md
* diagramas/04-diagramas-actividades/04-actividad-solicitar-turno.png
* diagramas/05-diagramas-secuencia/05-secuencia-solicitar-turno-escenario-01.png
* Tarjetas CRC de las clases involucradas.

### Prompt Utilizado
> Actúa como un Analista Funcional experto en UML y POO. Basado en el boceto inicial, las tarjetas CRC, el diagrama de casos de uso, actividades y secuencia proporcionados en el contexto, genera el código PlantUML para el diagrama de clases específico del Caso de Uso 1: Solicitar Turno.

### Ajustes Manuales Realizados
| Línea(s) Modificada(s) en PlantUML | Justificación del Cambio |
| :--- | :--- |
| class Paciente { ... } | Se eliminó el método solicitarTurno() de Paciente para centralizar el registro en Sistema, cumpliendo el Principio SRP. |
| class Doctor { ... } y Agenda "1" --> "*" Doctor | Se modeló la entidad concreta Doctor (matrícula, especialidad) en lugar de utilizar un atributo String doctorId dentro de Agenda. |
| interface INotificacion e interface IPersistencia | Se transformaron las clases concretas de servicio en interfaces para implementar el Principio DIP. |

### Decisiones de Diseño Justificadas (SOLID) y Simplificación

Principio SRP (Responsabilidad Única). La responsabilidad de instanciar, validar y conformar el objeto Turno recae enteramente sobre la clase Sistema, mientras que la clase Paciente actúa únicamente como proveedor de datos personales sin participar en la lógica de creación o gestión de turnos. Este cambio responde al Principio de Responsabilidad Única, que establece que una clase debe tener una única razón para cambiar. En el contexto del Caso de Uso 1, Paciente debe cambiar solo si sus atributos de identidad se modifican, pero la lógica de generación de turnos depende de factores externos como la disponibilidad del doctor y los horarios del sistema. Centralizar esta responsabilidad en Sistema asegura que Paciente permanezca estable y cohesivo, y cuando en el futuro sea necesario modificar el algoritmo de asignación de turnos, agregar políticas de prioridad o implementar optimizaciones, solo la clase Sistema será modificada sin impactar otras entidades del modelo.

Principio DIP (Inversión de Dependencias). En lugar de acoplar la clase Sistema directamente a clases concretas de persistencia o servicios de notificación específicos, se crearon las interfaces abstractas INotificacion e IPersistencia que garantizan la inversión de dependencias. Conforme al Principio de Inversión de Dependencias, el módulo de alto nivel Sistema no debe conocer si la base de datos es PostgreSQL, MongoDB o un archivo JSON, ni si las notificaciones se envían por correo, SMS o notificaciones push. Esta desacoplamiento permite cambiar la estrategia de persistencia o notificación sin modificar la lógica central del sistema, lo que resulta en una aplicación extensible y testeable donde se pueden crear múltiples implementaciones de las interfaces que el sistema utiliza de manera intercambiable, facilitando además que las pruebas unitarias inyecten mock objects para verificar el comportamiento de Sistema sin depender de infraestructura real.

Simplificación del Modelo (Remoción de Jerarquía Usuario). Se decidió remover la clase abstracta genérica Usuario que estaba diseñada para ser heredada por Secretaria, Doctor, Paciente y otras entidades, modelando en su lugar cada entidad como una clase concreta independiente con sus atributos y responsabilidades específicas. La jerarquía Usuario resultaba demasiado genérica y no aportaba funcionalidad compartida significativa en el contexto del Caso de Uso 1, porque las características de autenticación, permisos y roles que normalmente se centralizarían en una clase base no son relevantes en este escenario específico. Además, la herencia profunda crea acoplamiento frágil donde cambios en la superclase impactan indebidamente a todas las subclases. Al eliminar esta jerarquía innecesaria, el diagrama de clases resulta más limpio, más directo en su representación de conceptos del dominio, y más fácil de mantener, evitando la abstracción prematura y permitiendo introducir de manera gradual una clase base Usuario en el futuro si la autenticación global es requerida, sin disrumpción alguna dado el bajo acoplamiento actual.
