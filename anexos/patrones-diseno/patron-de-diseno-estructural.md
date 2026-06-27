# Anexo - Aplicación de Patrón de Diseño Estructural - Facade

## Patrones de Diseño Estructurales y su relación con SOLID

Los patrones de diseño estructurales ayudan a organizar la forma en que las clases y objetos se relacionan entre sí. Su objetivo principal es reducir acoplamiento, ordenar dependencias y facilitar que el sistema pueda crecer sin que cada cambio obligue a modificar muchas clases a la vez.

En relación con SOLID, estos patrones refuerzan especialmente:

- **SRP:** cada clase mantiene una responsabilidad concreta, mientras la estructura general distribuye mejor las colaboraciones.
- **OCP:** el sistema puede extenderse agregando nuevos componentes sin modificar en exceso los clientes existentes.
- **LSP:** tiene una incidencia menor en esta solución, porque el patrón `Facade` no se apoya en reemplazar subtipos dentro de una jerarquía, sino en ordenar el acceso a varios subsistemas mediante composición y delegación.
- **DIP:** las clases de alto nivel pueden trabajar contra abstracciones o puntos de entrada estables, sin depender directamente de todos los detalles internos.
- **ISP:** los clientes no necesitan conocer operaciones que no usan; acceden a una interfaz más simple y enfocada.

Para el Sistema de Turnos Médicos se selecciona el patrón **Facade** porque permite ofrecer una interfaz unificada para las operaciones principales del sistema y ocultar la complejidad de los subsistemas internos.

## Propósito y Tipo del Patrón

**Propósito:** simplificar el acceso a los casos de uso principales del sistema, evitando que los actores o clases cliente deban coordinar directamente objetos como `Agenda`, `Turno`, `SalaEspera`, `PersistenciaService`, `ServicioNotificaciones`, `ServicioAutenticacion` y `AuditoriaService`.

**Tipo:** `Facade`, patrón estructural GoF. Es adecuado porque el problema no está en la creación de objetos ni en un algoritmo particular, sino en la estructura de colaboración entre muchas clases. La fachada concentra una entrada de alto nivel y delega el trabajo específico en los subsistemas correspondientes.

## Descarte de otros patrones estructurales

Se elige `Facade` por sobre otros patrones estructurales porque el problema central es simplificar la relación entre clientes y un conjunto de subsistemas. Los demás patrones GoF estructurales no resuelven con la misma precisión este caso:

- **Adapter:** sirve para adaptar interfaces incompatibles, normalmente cuando un componente debe integrarse con otro que ya tiene una forma de uso distinta. En este sistema las clases del modelo (`Agenda`, `Turno`, `SalaEspera`, servicios internos y usuarios) ya pueden colaborar entre sí, por lo que no hay una incompatibilidad de interfaces que traducir.
- **Bridge:** separa una abstracción de su implementación para permitir que ambas evolucionen en jerarquías paralelas. El problema analizado no presenta dos jerarquías paralelas que deban independizarse, sino varios subsistemas que necesitan ser coordinados desde una entrada común.
- **Composite:** modela estructuras parte-todo con forma de árbol y permite tratar objetos simples y compuestos de manera uniforme. La dificultad del sistema no está en representar una jerarquía de componentes, sino en ordenar el acceso a operaciones distribuidas entre varias clases.
- **Decorator:** agrega responsabilidades dinámicamente a un objeto sin modificar su clase. En este caso no se busca sumar comportamientos variables en tiempo de ejecución, sino ocultar la complejidad de coordinación detrás de una interfaz más simple.
- **Proxy:** controla el acceso a un objeto específico, por ejemplo para diferir su creación, protegerlo o registrar su uso. El caso del Sistema de Turnos Médicos involucra varias clases internas trabajando en conjunto, no el acceso controlado a un único objeto.

Por estos motivos, `Facade` resulta el patrón más adecuado: no modifica la responsabilidad de cada subsistema, pero ofrece a `Secretaria`, `Paciente` y `Doctor` una forma de uso más clara y menos acoplada.

## Motivación

En el diseño del sistema existen varios casos de uso que requieren la colaboración de múltiples clases. Por ejemplo, solicitar un turno no implica solamente crear un objeto `Turno`; también puede requerir validar disponibilidad en `Agenda`, asociar paciente y doctor, guardar cambios en `PersistenciaService`, enviar una notificación y registrar un evento de auditoría.

Sin una fachada, clases cliente como `Secretaria`, `Paciente` o `Doctor` deberían conocer demasiados detalles del funcionamiento interno. Esto generaría un acoplamiento alto, porque cada cliente tendría que saber qué clases intervienen, en qué orden se usan y qué responsabilidades tiene cada una.

El patrón **Facade** resuelve este problema ubicando a `Sistema` como punto de entrada unificado. La clase `Sistema` expone operaciones de negocio comprensibles, como `registrarPaciente`, `solicitarTurno`, `cancelarTurno`, `registrarLlegadaPaciente` y `verAgendaDoctor`. Internamente, coordina las clases necesarias, pero los clientes no quedan obligados a conocer esa estructura.

## Estructura de Clases

Solo se incluyen las clases directamente relacionadas con la aplicación del patrón. El objetivo del diagrama es mostrar la estructura de acceso simplificada y la separación entre clientes, fachada y subsistemas internos.

El diagrama se organiza en tres paquetes principales:

- **Clientes del sistema:** agrupa 3 clases (`Secretaria`, `Paciente` y `Doctor`). Representa a los actores internos o externos que necesitan acceder a operaciones del sistema sin conocer la coordinación completa de objetos del dominio.
- **Fachada:** contiene 1 clase (`Sistema`). Esta clase concentra la interfaz de alto nivel del patrón y expone operaciones como `registrarPaciente`, `solicitarTurno`, `cancelarTurno`, `registrarLlegadaPaciente` y `verAgendaDoctor`.
- **Subsistemas internos:** agrupa 7 clases (`ServicioAutenticacion`, `Agenda`, `Turno`, `SalaEspera`, `PersistenciaService`, `ServicioNotificaciones` y `AuditoriaService`). Cada una conserva una responsabilidad específica del modelo, mientras `Sistema` coordina su uso según el caso de uso solicitado.

Esta organización permite leer el diagrama aun sin renderizar la imagen: los clientes dependen de una única entrada visible, la fachada centraliza la coordinación y los subsistemas quedan ubicados detrás de esa interfaz simplificada.

[Estructura de clases con diagrama UML](../../diagramas/01-diagrama-clases/01-patron-estructural-facade.png)

## Justificación Técnica de la Estructura de Clases

### Clase `Sistema` como Facade

`Sistema` actúa como la fachada del modelo. Su responsabilidad es ofrecer operaciones de alto nivel para ejecutar los casos de uso principales sin exponer toda la red de colaboraciones internas.

Es necesaria porque centraliza el acceso al sistema desde una interfaz simple. Por ejemplo, `solicitarTurno` representa una operación del negocio que puede involucrar validación de disponibilidad, creación o actualización de `Turno`, persistencia, notificación y auditoría.

### Clases cliente

`Secretaria`, `Paciente` y `Doctor` representan usuarios que necesitan interactuar con el sistema. Con la fachada, estos clientes no deben conocer directamente la secuencia completa de objetos internos. Esto evita duplicación de coordinación y reduce el impacto de cambios futuros.

La `Secretaria` puede registrar pacientes, programar turnos, cancelar turnos, registrar llegadas y consultar agendas. El `Paciente` puede solicitar, cancelar o consultar turnos. El `Doctor` puede ver su agenda y consultar pacientes en espera. En todos los casos, la fachada les entrega una entrada más clara al sistema.

### Subsistemas internos

#### `ServicioAutenticacion`

Su responsabilidad específica es validar las credenciales de los usuarios antes de permitir el acceso a las operaciones del sistema. La fachada lo utiliza principalmente en `iniciarSesion`, porque el inicio de sesión es la puerta de entrada previa a cualquier acción operativa.

#### `Agenda`

Su responsabilidad específica es administrar disponibilidad, turnos del día y franjas horarias asociadas al doctor. Interviene en `solicitarTurno`, cuando la fachada necesita verificar si existe disponibilidad antes de crear la reserva, y en `verAgendaDoctor`, cuando se consultan los turnos asociados a una fecha.

#### `Turno`

Su responsabilidad específica es representar y controlar el ciclo de vida del turno: creación, confirmación, cancelación y cambio de estado. Interviene en `solicitarTurno`, `cancelarTurno` y `registrarLlegadaPaciente`, ya que esas operaciones modifican o consultan el estado del turno.

#### `SalaEspera`

Su responsabilidad específica es administrar los pacientes que ya llegaron al centro de salud y esperan ser atendidos. Interviene en `registrarLlegadaPaciente`, donde la fachada coordina el pasaje del paciente desde un turno válido hacia la sala de espera.

#### `PersistenciaService`

Su responsabilidad específica es guardar, buscar y actualizar información del sistema. Interviene internamente en `registrarPaciente`, `solicitarTurno`, `cancelarTurno` y `registrarLlegadaPaciente`, porque esas operaciones requieren conservar o recuperar datos del dominio sin obligar al cliente a solicitar una persistencia manual.

#### `ServicioNotificaciones`

Su responsabilidad específica es comunicar eventos relevantes a los usuarios, como confirmaciones, recordatorios o cancelaciones. Interviene en `solicitarTurno`, `cancelarTurno` y `registrarLlegadaPaciente`, cuando la fachada necesita informar un cambio importante en el estado del proceso.

#### `AuditoriaService`

Su responsabilidad específica es registrar trazabilidad de operaciones relevantes del sistema. La fachada lo necesita porque operaciones como `registrarPaciente`, `solicitarTurno`, `cancelarTurno` y `registrarLlegadaPaciente` modifican información sensible del proceso de atención y conviene dejar constancia de esas acciones.

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

