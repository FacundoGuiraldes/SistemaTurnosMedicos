# Anexo - Aplicación de Patrón de Diseño Estructural - Facade

## Patrones de Diseño Estructurales y su relación con SOLID

Los patrones de diseño estructurales ayudan a organizar la forma en que las clases y objetos se relacionan entre sí. Su objetivo principal es reducir acoplamiento, ordenar dependencias y facilitar que el sistema pueda crecer sin que cada cambio obligue a modificar muchas clases a la vez.

En relación con SOLID, estos patrones refuerzan especialmente:

- **SRP:** cada clase mantiene una responsabilidad concreta, mientras la estructura general distribuye mejor las colaboraciones.
- **OCP:** el sistema puede extenderse agregando nuevos componentes sin modificar en exceso los clientes existentes.
- **DIP:** las clases de alto nivel pueden trabajar contra abstracciones o puntos de entrada estables, sin depender directamente de todos los detalles internos.
- **ISP:** los clientes no necesitan conocer operaciones que no usan; acceden a una interfaz más simple y enfocada.

Para el Sistema de Turnos Médicos se selecciona el patrón **Facade** porque permite ofrecer una interfaz unificada para las operaciones principales del sistema y ocultar la complejidad de los subsistemas internos.

## Propósito y Tipo del Patrón

**Propósito:** simplificar el acceso a los casos de uso principales del sistema, evitando que los actores o clases cliente deban coordinar directamente objetos como `Agenda`, `Turno`, `SalaEspera`, `PersistenciaService`, `ServicioNotificaciones`, `ServicioAutenticacion` y `AuditoriaService`.

**Tipo:** `Facade`, patrón estructural GoF. Es adecuado porque el problema no está en la creación de objetos ni en un algoritmo particular, sino en la estructura de colaboración entre muchas clases. La fachada concentra una entrada de alto nivel y delega el trabajo específico en los subsistemas correspondientes.

## Motivación

En el diseño del sistema existen varios casos de uso que requieren la colaboración de múltiples clases. Por ejemplo, solicitar un turno no implica solamente crear un objeto `Turno`; también puede requerir validar disponibilidad en `Agenda`, asociar paciente y doctor, guardar cambios en `PersistenciaService`, enviar una notificación y registrar un evento de auditoría.

Sin una fachada, clases cliente como `Secretaria`, `Paciente` o `Doctor` deberían conocer demasiados detalles del funcionamiento interno. Esto generaría un acoplamiento alto, porque cada cliente tendría que saber qué clases intervienen, en qué orden se usan y qué responsabilidades tiene cada una.

El patrón **Facade** resuelve este problema ubicando a `Sistema` como punto de entrada unificado. La clase `Sistema` expone operaciones de negocio comprensibles, como `registrarPaciente`, `solicitarTurno`, `cancelarTurno`, `registrarLlegadaPaciente` y `verAgendaDoctor`. Internamente, coordina las clases necesarias, pero los clientes no quedan obligados a conocer esa estructura.

## Estructura de Clases

Solo se incluyen las clases directamente relacionadas con la aplicación del patrón. El objetivo del diagrama es mostrar la estructura de acceso simplificada y la separación entre clientes, fachada y subsistemas internos.

[Estructura de clases con diagrama UML](../../diagramas/01-diagrama-clases/01-patron-estructural-facade.png)

## Justificación Técnica de la Estructura de Clases

### Clase `Sistema` como Facade

`Sistema` actúa como la fachada del modelo. Su responsabilidad es ofrecer operaciones de alto nivel para ejecutar los casos de uso principales sin exponer toda la red de colaboraciones internas.

Es necesaria porque centraliza el acceso al sistema desde una interfaz simple. Por ejemplo, `solicitarTurno` representa una operación del negocio que puede involucrar validación de disponibilidad, creación o actualización de `Turno`, persistencia, notificación y auditoría.

### Clases cliente

`Secretaria`, `Paciente` y `Doctor` representan usuarios que necesitan interactuar con el sistema. Con la fachada, estos clientes no deben conocer directamente la secuencia completa de objetos internos. Esto evita duplicación de coordinación y reduce el impacto de cambios futuros.

La `Secretaria` puede registrar pacientes, programar turnos, cancelar turnos, registrar llegadas y consultar agendas. El `Paciente` puede solicitar, cancelar o consultar turnos. El `Doctor` puede ver su agenda y consultar pacientes en espera. En todos los casos, la fachada les entrega una entrada más clara al sistema.

### Subsistemas internos

`Agenda` mantiene la responsabilidad de disponibilidad, organización y consulta de turnos. `Turno` conserva el ciclo de vida del turno, incluyendo confirmación, cancelación y paso a estado de espera. `SalaEspera` administra la llegada y permanencia de pacientes. `PersistenciaService` se ocupa de guardar y recuperar información. `ServicioNotificaciones` informa eventos relevantes. `ServicioAutenticacion` valida accesos. `AuditoriaService` registra trazabilidad.

Estas clases no desaparecen ni pierden responsabilidad. La fachada solo ordena el acceso a ellas para que los clientes no deban acoplarse a todos los detalles.

### Flujo estructural

1. Un cliente solicita una operación de alto nivel a `Sistema`.
2. `Sistema` interpreta el caso de uso y coordina las clases internas necesarias.
3. Cada subsistema ejecuta su responsabilidad específica.
4. `Sistema` devuelve el resultado al cliente sin exponer la complejidad interna.

Por ejemplo, al cancelar un turno, el cliente invoca `cancelarTurno` sobre `Sistema`. La fachada busca el turno mediante persistencia, delega el cambio de estado en `Turno`, actualiza la información, registra auditoría y solicita una notificación. El cliente no necesita conocer ese flujo completo.

## Beneficios para el diseño

- Reduce el acoplamiento entre usuarios del sistema y subsistemas internos.
- Evita duplicar lógica de coordinación en `Secretaria`, `Paciente` y `Doctor`.
- Mantiene las reglas de negocio distribuidas en clases del dominio.
- Facilita incorporar cambios internos sin alterar la forma en que los clientes usan el sistema.
- Hace más claro el diagrama de clases al separar clientes, fachada y subsistemas.

