# Bitácora de IA - Analista Funcional CU 1

### Archivos de Contexto Utilizados
* `diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw`
* `diagramas/02-casos-de-uso/02-caso-uso-solicitar-turno.png`
* `diagramas/03-escenarios-casos-de-uso/03-solicitar-turno-escenario-01.md`
* `diagramas/04-diagramas-actividades/04-actividad-solicitar-turno.png`
* `diagramas/05-diagramas-secuencia/05-secuencia-solicitar-turno-escenario-01.png`
* Tarjetas CRC de las clases involucradas.

### Prompt Utilizado
> Actúa como un Analista Funcional experto en UML y POO. Basado en el boceto inicial, las tarjetas CRC, el diagrama de casos de uso, actividades y secuencia proporcionados en el contexto, genera el código PlantUML para el diagrama de clases específico del Caso de Uso 1: Solicitar Turno.

### Ajustes Manuales Realizados
| Línea(s) Modificada(s) en PlantUML | Justificación del Cambio |
| :--- | :--- |
| `class Paciente { ... }` | Se eliminó el método `solicitarTurno()` de Paciente para centralizar el registro en `Sistema`, cumpliendo el Principio SRP. |
| `class Doctor { ... }` y `Agenda "1" --> "*" Doctor` | Se modeló la entidad concreta `Doctor` (matrícula, especialidad) en lugar de utilizar un atributo String `doctorId` dentro de `Agenda`. |
| `interface INotificacion` e `interface IPersistencia` | Se transformaron las clases concretas de servicio en interfaces para implementar el Principio DIP. |

### Decisiones de Diseño Justificadas (SOLID) y Simplificación
1. **Principio SRP:** La responsabilidad de instanciar y conformar el objeto `Turno` recae enteramente sobre la clase `Sistema`. El `Paciente` actúa solo como proveedor de datos, evitando que una entidad asuma responsabilidades de gestión que no le corresponden.
2. **Principio DIP:** En lugar de acoplar `Sistema` a clases concretas para la base de datos o el gestor de correos, se segregaron las interfaces `INotificacion` e `IPersistencia`, asegurando que el módulo de alto nivel dependa de abstracciones.
3. **Simplificación del Modelo (Remoción de Jerarquía Usuario):** Se decidió remover la clase abstracta genérica `Usuario` y su herencia directa (`Secretaria`, `Paciente`) que venía del boceto inicial. Esta decisión de diseño se toma para simplificar el flujo del CU1 y evitar sobrecargar el diagrama con jerarquías abstractas que no aportan funcionalidad directa en el escenario específico de Solicitar Turno.

