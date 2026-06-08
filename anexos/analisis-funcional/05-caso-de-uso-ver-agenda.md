# Caso de Uso N°5 - Ver Agenda

---

## 1. Descripción y Trazabilidad con Requisitos Funcionales

**Actor/es:** Doctor, Secretaria

**Objetivo:** Permite al doctor visualizar su agenda con los turnos programados de un día determinado. 

**Flujo principal:**

1. El doctor accede al sistema. | El doctor ingresa con credenciales válidas. |
2. El sistema muestra el menú de opciones disponibles. | El sistema ofrece un calendario o selector de fecha. |
3. El doctor selecciona la opción “Ver agenda”. | El doctor elige un día específico. |
4. El doctor selecciona el día que desea consultar. | El sistema despliega la agenda completa de ese día. |
5. El sistema muestra la agenda con los turnos, pacientes y horarios correspondientes. | La agenda incluye información relevante como nombre del paciente, hora del turno y motivo de consulta. |

**Requisitos funcionales que satisface:**

| ID | Requisito Funcional (texto exacto de introduccion.md) | Cómo lo satisface este caso de uso |
|----|------------------------------------------------------|-------------------------------------|
|* **RF2 Visualizar agenda:** | El sistema debe ofrecer la visualización de un calendario u cronograma con la agenda del profesional médico. | Este caso de uso se centra en la funcionalidad de visualizar la agenda del doctor, permitiéndole seleccionar un día específico y mostrar los turnos programados, cumpliendo así con el requisito de ofrecer una visualización clara y organizada de la agenda médica. |
| * **RF4 Gestión de disponibilidad y bloqueo:** | El sistema debe permitir bloquear días y/o horarios dependiendo la disponibilidad del médico, evitando la asignación de turnos en vacaciones, feriados, horarios con compromisos, etc. | Este caso de uso permite al doctor gestionar su disponibilidad y bloquear días o horarios según su calendario, cumpliendo con el requisito de manejar la disponibilidad del profesional médico. |
| * **RF5 Check de asistencia:** | El sistema debe permitir marcar con un check los pacientes que efectivamente han asistido a su turno médico, incluyendo hora de llegada y lista de espera. | Este caso de uso permite al doctor visualizar la agenda y marcar la asistencia de los pacientes, cumpliendo con el requisito de gestionar la asistencia a los turnos médicos.

---

## 2. Diagrama de Casos de Uso

![Diagrama de Casos de Uso - [Ver Agenda]](../../diagramas/02-casos-de-uso/02-caso-uso-ver-agenda-05/02-caso-uso-ver-agenda-05.png)

**Actores y relaciones:**
- [Doctor] → utiliza la funcionalidad para consultar la agenda de atención y visualizar los turnos asignados para una fecha determinada. Además, puede realizar acciones complementarias sobre la agenda, como bloquear horarios cuando sea necesario.
- [Secretaria] → accede a la agenda para gestionar la programación de turnos, verificar disponibilidad y brindar información operativa relacionada con la atención médica.
- Include/Extend: <<include>>: se utiliza entre Ver agenda y Consultar turnos del día porque la consulta de los turnos es una actividad obligatoria para poder visualizar la agenda. La agenda no puede mostrarse sin recuperar previamente la información de los turnos programados.
<<extend>>: se utiliza entre Bloquear horario y Ver agenda porque el bloqueo de horarios representa un comportamiento opcional que puede ejecutarse a partir de la visualización de la agenda, pero no forma parte del flujo básico necesario para consultar los turnos.

---

## 3. Diagrama de Actividades

![Diagrama de Actividades - [Ver Agenda]](../../diagramas/04-diagramas-actividades/04-actividad-ver-agenda-05.png)

**Swimlanes:** Se utilizaron tres carriles: Doctor, Sistema y Base de Datos. La distribución separa claramente las responsabilidades de cada participante. El Doctor inicia la consulta y selecciona el período que desea visualizar; el Sistema gestiona la autenticación, procesa la solicitud y construye la vista de la agenda; mientras que la Base de Datos se encarga exclusivamente de recuperar la información de los turnos almacenados. Esta separación permite distinguir las acciones de negocio de las operaciones de persistencia de datos.

**Decisiones clave del flujo:** - Autenticación del doctor: el sistema verifica si las credenciales son válidas. Esta decisión determina si el usuario puede acceder a la funcionalidad o debe corregir sus datos de acceso.
- Existencia de turnos para la fecha seleccionada: la base de datos evalúa si existen registros asociados al día consultado. Si no hay turnos, el sistema informa que la agenda está vacía; si existen, recupera la información necesaria para construir la agenda.
- Selección de una nueva fecha ante agenda vacía: cuando no se encuentran turnos para el día elegido, el flujo permite al doctor consultar otra fecha sin abandonar el proceso, facilitando la navegación entre distintos períodos de la agenda.

---

## 4. Diagrama de Secuencia

![Diagrama de Secuencia - [Ver Agenda]](../../diagramas/05-diagramas-secuencia/05-secuencia-ver-agenda-ver-agenda-exitoso-05.png)

**Participantes:** 
- Doctor: actor externo que inicia la consulta de la agenda y solicita información adicional sobre pacientes asociados a los turnos.
- :Sistema: instancia representada con la notación :Objeto, responsable de coordinar la consulta, solicitar información a las demás clases y devolver los resultados al doctor.
- agenda:Agenda: objeto de la clase Agenda representado con la notación objeto:Clase, creado para construir y gestionar la agenda correspondiente a la fecha seleccionada.
- turno:Turno: objeto de la clase Turno representado con la notación objeto:Clase, utilizado para recuperar los detalles de cada turno y la información de los pacientes asociados.

**Mensajes clave:**
- [accederAlSistema(numeroLicencia)] → inicia el proceso de autenticación y acceso al sistema.
- [seleccionarVerAgenda()] → indica que el doctor desea consultar la agenda para una fecha determinada.
- [crearAgendaDelDia(fecha)] → desencadena la creación y preparación de la agenda correspondiente al día seleccionado.
- [obtenerTurnosDelDia(fecha)] → recupera los turnos programados para la fecha consultada.
- [obtenerDetalles()] → obtiene la información detallada de cada turno para construir la agenda.
- [consultarPacienteEspecifico(turno)] → permite profundizar la consulta sobre un turno particular seleccionado por el doctor.
- [obtenerInfoTurno(turno)] → recupera la información específica de un turno determinado.
- [obtenerInfoPaciente()] → obtiene los datos del paciente asociado al turno seleccionado para mostrar al doctor.

**Objetos temporales destruidos:** Los objetos agenda:Agenda y turno:Turno aparecen como objetos temporales dentro de esta interacción y son destruidos al finalizar el escenario (representado por la "X" al final de sus líneas de vida). Son temporales porque se crean para procesar la consulta de una agenda específica y recuperar la información necesaria durante la ejecución del caso de uso. Una vez que los datos fueron enviados al doctor, estos objetos dejan de participar en la interacción modelada.

---

## 5. Diagrama de Clases del Caso de Uso

![Diagrama de Clases - [Ver Agenda]](../../diagramas/01-diagrama-clases/05-clases-ver-agenda-05.png)

**Clases involucradas:**

| Clase | Responsabilidad (según tarjeta CRC) | Tarjeta CRC |
|-------|-------------------------------------|-------------|
| [Doctor] | Ver agenda diaria de turnos, consultar pacientes en sala de espera, Marcar pacientes atendidos, Definir disponibilidad general | [Tarjeta CRC - Doctor](../../herramientas-agile/tarjetas-crc/04-tarjeta-crc-doctor.md) |
| [Sistema] | validar colisiones de turnos y enviar recordatorio automático al paciente | [Tarjeta CRC - Sistema](../../herramientas-agile/tarjetas-crc/08-tarjeta-crc-sistema.md) |
| [Agenda] | Configurar reglas de disponibilidad, gestionar franjas horarias y validar turnos contra reglas horarias | [Tarjeta CRC - Agenda](../../herramientas-agile/tarjetas-crc/06-tarjeta-crc-agenda.md) |
| [Turno] | Mantener ciclo de vida de la cita, actualizar estado por llegada, proveer detalle completo de la cita.  | [Tarjeta CRC - Turno](../../herramientas-agile/tarjetas-crc/05-tarjeta-crc-turno.md) |
| [Paciente] | Consultar mis turnos programados, registrar mi llegada al consultorio  | [Tarjeta CRC - Paciente](../../herramientas-agile/tarjetas-crc/02-tarjeta-crc-paciente.md) |
| [Usuario] | Autenticarse en el sistema y modificar perfil personal| [Tarjeta CRC - Usuario](../../herramientas-agile/tarjetas-crc/01-tarjeta-crc-usuario.md) |

**Relaciones UML:**

| Relación | Clases | Justificación |
|----------|--------|---------------|
| [Herencia] | [Doctor] → [Usuario] | Se utiliza herencia porque el doctor comparte atributos y comportamientos generales de un usuario del sistema (identificación, acceso y gestión de perfil), especializando esa funcionalidad con responsabilidades propias del rol médico. |
| [Asociación] | [Doctor] → [Sistema] | Existe una interacción directa y permanente durante el caso de uso, ya que el doctor utiliza el sistema para consultar la agenda. No es una dependencia porque el doctor mantiene una relación funcional con el sistema durante la ejecución del proceso. |
| [Asociación] | [Sistema] → [Agenda] | El sistema solicita la agenda correspondiente a una fecha determinada y trabaja con ella para mostrar la información al doctor. La agenda tiene identidad propia dentro del dominio, por lo que no corresponde modelarla como dependencia temporal. |
| [Agregación] | [Agenda] → [Turno] | La agenda está compuesta por un conjunto de turnos, pero los turnos pueden seguir existiendo independientemente de una agenda específica. Por ello corresponde una agregación y no una composición.|
| [Asociación] | [Turno] → [Paciente] | Cada turno está vinculado a un paciente y necesita acceder a su información para mostrarla en la agenda. Se modela como asociación porque existe una relación de dominio persistente entre ambas entidades.|

---

## 6. Pseudocódigo

```text
INICIO Ver Agenda

// El doctor accede al sistema para consultar los turnos programados de una fecha específica de atención.

Doctor doctor = nuevo Doctor(numeroLicencia, especialidad, consultorio)
Sistema sistema = nuevo Sistema()
Agenda agenda = nuevo Agenda(fecha)
Turno turno = nuevo Turno()

// El sistema verifica que el doctor tenga credenciales válidas para acceder a la agenda médica.
accesoValido = sistema.accederAlSistema(numeroLicencia)

SI accesoValido es verdadero

    // El doctor selecciona la funcionalidad de ver agenda para consultar sus turnos programados.
    agenda = sistema.seleccionarVerAgenda()

    // El sistema construye la agenda correspondiente al día seleccionado.
    agenda.crearAgendaDelDia(fecha)

    // La agenda obtiene los turnos programados para la fecha consultada.
    listaTurnosProgramados = agenda.obtenerTurnosDelDia(fecha)

    SI listaTurnosProgramados contiene turnos

        // La agenda recupera los detalles necesarios de cada turno para mostrar la grilla del día.
        detallesTurno = turno.obtenerDetalles()

        // El doctor puede consultar información específica de un paciente asociado a un turno.
        infoPaciente = sistema.consultarPacienteEspecifico(turno)

        // La agenda obtiene la información del turno seleccionado.
        infoTurno = agenda.obtenerInfoTurno(turno)

        // El turno recupera la información del paciente vinculado.
        detallesPaciente = turno.obtenerInfoPaciente()

        // El sistema devuelve la agenda completa con turnos, pacientes y horarios.
        Retornar agenda

    SINO

        // El flujo alternativo se activa cuando no existen turnos programados para la fecha seleccionada.
        Retornar "No hay turnos programados para el día seleccionado"

    FIN SI

SINO

    // El flujo alternativo se activa cuando el doctor no logra autenticarse correctamente.
    Retornar "Credenciales incorrectas. Intente nuevamente"

FIN SI

FIN
```
