# Diagramas de Clases

* [Diagrama de Clases - Boceto Inicial](./01-boceto-inicial.excalidraw)
* Principios SOLID
  * [Diagrama de Clases - SRP (Single Responsibility Principle)](./01-solid-01-srp.puml)
  * [Diagrama de Clases - OCP (Open/Closed Principle)](./01-solid-02-ocp.puml)
  * [Diagrama de Clases - LSP (Liskov Substitution Principle)](./01-solid-03-lsp.puml)
  * [Diagrama de Clases - ISP (Interface Segregation Principle)](./01-solid-04-isp.puml)
  * [Diagrama de Clases - DIP (Dependency Inversion Principle)](./01-solid-05-dip.puml)

### 2. Diagramas de Clases por Caso de Uso (Módulo Técnico)

| Caso de Uso | Archivo Fuente | Diagrama Renderizado | Descripción |
| :--- | :--- | :--- | :--- |
| **CU1: Registrar Turno** | `01-clases-solicitar-turno.puml` | `01-clases-solicitar-turno.png` | Estructura base orientada a objetos para la gestión e instanciación de turnos médicos (Especialista: Valeria Silva). |
| **CU2: Cancelar turno** | `02-clases-cancelar-turno-02.puml` | `02-clases-cancelar-turno-02.png` | Modelado de clases del flujo de baja de citas, liberación de bloques horarios e inversión de dependencias para alertas. |
| **CU3: Registrar llegada del paciente** | `03-clases-registrar-llegada-03.puml` | `03-clases-registrar-llegada-03.png` | Modelado de clases del flujo de admisión en sala de espera, integrando estados de turnos y acoplamiento abstracto. |
| **CU4: Registrar paciente** | `04-clases-registrar-paciente-04.puml` | `04-clases-registrar-paciente-04.png` | Modelado de clases del flujo de registro de nuevos pacientes, incluyendo validación de datos y creación de cuentas de usuario. |
| **CU5: Ver agenda** | `05-clases-ver-agenda-05.puml` | `05-clases-ver-agenda-05.png` | Modelado de clases del flujo de visualización de la agenda médica, permitiendo a los usuarios consultar turnos programados y disponibilidad. |

---

# Diagrama de Clases Final - Sistema de Turnos Médicos

## 1. Versión del Diagrama

| Versión | Casos de uso integrados | Fecha |
|---------|------------------------|-------|
| v1 | CU1 Solicitar Turno, CU2 Cancelar Turno, CU3 Registrar Llegada, CU4 Registrar Paciente, CU5 Ver Agenda | 2026-06-07 |
| v2 | Integración de inconsistencias detectadas en CU2, CU3, CU4 y CU5 | 2026-06-15 |

## 2. Diagrama

![Diagrama de Clases Final](06-clases-diagrama-final.png)

## 3. Clases del Sistema

| Clase | Responsabilidad (según tarjeta CRC) | Aparece en CU |
|-------|-------------------------------------|---------------|
| Usuario | Representar un actor del sistema con datos de identidad y capacidades de autenticación. | CU1, CU2, CU3, CU4, CU5 |
| Paciente | Registrar datos de paciente, solicitar y cancelar turnos, consultar turnos y registrar llegada. | CU1, CU2, CU3 |
| Secretaria | Registrar pacientes, gestionar turnos, consultar agendas y registrar llegadas. | CU1, CU2, CU3, CU4 |
| Doctor | Visualizar agenda, consultar pacientes en espera y registrar diagnósticos. | CU3, CU4, CU5 |
| Turno | Modelar la cita médica con fecha, hora, estado, paciente, doctor y especialidad. | CU1, CU2, CU3, CU4, CU5 |
| Agenda | Controlar la disponibilidad del doctor, los horarios bloqueados y los turnos del día. | CU1, CU4, CU5 |
| SalaEspera | Organizar pacientes presentes en la sala de espera y registrar su estado. | CU3 |
| LlegadaPaciente | Validar la llegada del paciente, detectar su turno y notificar ingreso a la sala de espera. | CU3 |
| Sistema | Orquestar autenticación, reservas, cancelaciones, notificaciones y persistencia. | CU1, CU2, CU3, CU4, CU5 |
| ServicioAutenticacion | Autenticar usuarios del sistema para habilitar el acceso. | CU1 |
| ServicioNotificaciones | Enviar alertas y recordatorios a pacientes. | CU5 |
| PersistenciaService | Persistir entidades del dominio como usuarios, turnos y agendas. | CU1, CU2, CU3, CU4, CU5 |
| AuditoriaService | Registrar eventos de auditoría técnica en los procesos del sistema. | CU1, CU2, CU3, CU4, CU5 |
| Especialidad | Definir la especialidad médica asociada a doctores y turnos. | CU1, CU4, CU5 |
| Notificacion | Representar mensajes enviados al paciente sobre el turno. | CU5 |

## 4. Decisiones de Integración

| Inconsistencia encontrada | Decisión tomada | Justificación |
|--------------------------|-----------------|---------------|
| `Usuario` no tenía atributo `apellido: String` (presente en CU2 y CU3) | Se agregó `- apellido: String` a `Usuario` | Es un dato de identidad básico que debe estar en la clase base |
| `Turno` no tenía atributo `asistencia: Boolean` (presente en CU3) | Se agregó `- asistencia: Boolean` a `Turno` | Necesario para registrar si el paciente se presentó al turno |
| `Turno` no tenía métodos `getPaciente()` ni `obtenerInfoPaciente()` (presentes en CU2, CU3 y CU5) | Se agregaron ambos métodos a `Turno` | Son operaciones requeridas por múltiples casos de uso |
| `Agenda` no tenía atributo `id: String` (presente en CU2) | Se agregó `- id: String` a `Agenda` | Necesario para identificar unívocamente cada agenda |
| `Agenda` no tenía métodos `crearAgendaDelDia()` ni `validarTurnosContraReglas()` (presentes en CU5) | Se agregaron ambos métodos a `Agenda` | Operaciones requeridas por el flujo de visualización de agenda |
| `SalaEspera` no tenía atributo `id: String` y usaba `pacientes` en lugar de `pacientesEnEspera` (CU3) | Se agregó `- id: String` y se renombró el atributo a `pacientesEnEspera` | Consistencia con el diagrama parcial de CU3 |
| `SalaEspera` no tenía método `agregarPaciente()` (presente en CU3) | Se agregó `+ agregarPaciente(paciente: Paciente): void` | Operación requerida por el flujo de admisión |
| `Doctor` no tenía métodos `marcarPacienteAtendido()` ni `definirDisponibilidad()` (presentes en CU5) | Se agregaron ambos métodos a `Doctor` | Operaciones requeridas por el flujo de gestión de agenda |
| `Doctor.autorizarSobreturno()` no tenía parámetro `agenda: Agenda` (presente en CU5) | Se actualizó la firma a `autorizarSobreturno(agenda: Agenda): boolean` | Consistencia con el diagrama parcial de CU5 |
| `Doctor.registrarDiagnostico()` tenía firma incompatible con CU5 | Se unificó a `registrarDiagnostico(turno: Turno, diagnostico: String): void` | El parámetro `Turno` es más expresivo que `turnoId: String` |
| `Doctor.verAgenda()` retornaba `Agenda` en CU5 pero `List<Turno>` en el final | Se mantuvo `List<Turno>` en el diagrama final | Retornar la lista de turnos es más útil para el consumidor que retornar la entidad Agenda completa |
| `Doctor.consultarPacientesSalaEspera()` en CU5 difiere de `consultarPacientesEsperando()` en el final | Se mantuvo `consultarPacientesEsperando()` en el diagrama final | El nombre es más expresivo y consistente con el contexto de sala de espera del sistema |
| `Agenda.obtenerInfoTurno(turno: Turno): Map<String,String>` en CU5 difiere de `obtenerInfoTurno(turnoId: String): Turno` en el final | Se mantuvo la firma del final con `turnoId: String` y retorno `Turno` | Pasar el ID es suficiente para buscar el turno y retornar la entidad completa es más expresivo que un Map |
| `Turno.obtenerDetalles(): Map<String,String>` en CU5 difiere de `getDetalles(): String` en el final | Se mantuvo `getDetalles(): String` en el diagrama final | Una representación en String es más simple y suficiente para el nivel de detalle requerido en el sistema |
| `Secretaria` no tenía métodos `solicitarDatosPersonales()` ni `validarDatos()` (presentes en CU4) | Se agregaron ambos métodos a `Secretaria` | Operaciones requeridas por el flujo de registro de pacientes |
| `EstadoTurno` no tenía valores `Pendiente` ni `Ausente` (presentes en CU2) | Se agregaron ambos valores al enum | Estados necesarios para el ciclo de vida completo del turno |
| `Sistema` no tenía métodos de CU4 y CU5: `seleccionarRegistrarPaciente()`, `validarDuplicidad()`, `crearCuentaUsuario()`, `accederAlSistema()`, `seleccionarVerAgenda()`, `consultarPacienteEspecifico()` | Se agregaron todos al `Sistema` | Operaciones de orquestación requeridas por CU4 y CU5 |
| Las interfaces DIP de los parciales (ITurnoRepository, IAgendaService, etc.) no están representadas en el final | Se decidió mantener clases de servicio concretas | El diagrama final prioriza claridad de la estructura de dominio sobre la representación de abstracciones técnicas |

## 5. Coherencia con Artefactos Previos

**Coherencia con boceto inicial (A1):**

El boceto inicial planteó la separación entre usuarios, turnos y agenda. El diagrama final conserva esa estructura base y añade la orquestación de servicios (`Sistema` y servicios transversales), así como las entidades auxiliares de presencia física (`SalaEspera`, `LlegadaPaciente`). Estos cambios son coherentes con el avance del análisis y no contradicen el diseño original.

**Coherencia con tarjetas CRC (A2):**

Las responsabilidades definidas en las CRC se reflejan directamente en las clases del diagrama. Por ejemplo, `Paciente` mantiene su rol de actor solicitante de turnos, `Secretaria` centraliza la gestión administrativa de agendas y `Doctor` mantiene la responsabilidad de ver agenda y atender pacientes. `Turno` actúa como la entidad colaboradora entre `Paciente`, `Doctor`, `Agenda` y `Especialidad`, tal como las CRC demandan.

**Coherencia con diagramas de secuencia (A3):**

Los mensajes intercambiados en los diagramas de secuencia respaldan los métodos presentes en el diagrama final. La reserva de turno, la validación de conflictos, el envío de notificaciones y la gestión de llegada del paciente se enlazan con operaciones como `solicitarTurno(...)`, `validarColisionTurno(...)`, `enviarRecordatorioAutomatico(...)`, `registrarLlegadaPaciente(...)` y `validarTurnoExistente(...)`.