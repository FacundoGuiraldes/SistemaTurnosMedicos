# Análisis de Casos de Uso
Este anexo documenta la correspondencia entre los casos de uso del sistema y el diagrama de clases final, mostrando cómo las entidades del dominio y sus colaboraciones soportan el flujo de cada caso.

### Registro de Anexos Desarrollados (Actividad N° 4)
| Caso de Uso | Documento de Análisis | Descripción Funcional |
| :--- | :--- | :--- |
| **CU2: Cancelar turno** | [`02-caso-de-uso-cancelar-turno.md`](02-caso-de-uso-cancelar-turno.md) | Análisis del flujo de baja de citas por Paciente o Secretaria, liberación de bloques horarios en la agenda médica y envío de notificaciones de cancelación. |
| **CU3: Registrar llegada del paciente** | [`03-caso-de-uso-registrar-llegada.md`](03-caso-de-uso-registrar-llegada.md) | Documentación completa del flujo de admisión física, reglas de asignación a sala de espera y pseudocódigo orientado a objetos. |

## CU1 - Solicitar Turno
Clases principales:
- `Paciente`
- `Agenda`
- `Doctor`
- `Turno`
- `Especialidad`
- `Sistema`

Descripción:
- `Paciente` inicia la búsqueda y selección de turno en una `Especialidad` concreta.
- `Agenda` responde con `obtenerTurnosDelDia(...)` y `sugerirProximasFranjasLibres(...)`.
- `Turno` es el resultado del proceso y resume la relación entre paciente, doctor y especialidad.
- `Sistema` orquesta la validación de disponibilidad con `validarColisionTurno(...)` y la creación del turno con `solicitarTurno(...)`.

## CU2 - Cancelar Turno
Clases principales:
- `Paciente`
- `Secretaria`
- `Turno`
- `Sistema`
- `Agenda`

Descripción:
- `Paciente` o `Secretaria` pueden invocar `cancelarTurno(...)` en `Turno`.
- `Turno` encapsula la lógica de cambio de estado y mantiene coherencia de su ciclo de vida.
- `Sistema` centraliza el proceso y delega la eliminación del turno en `Agenda` mediante `eliminarTurno(...)`.
- `Agenda` conserva su independencia de los datos personales del paciente y solo trabaja con la entidad `Turno`.

## CU3 - Registrar Llegada
Clases principales:
- `Paciente`
- `LlegadaPaciente`
- `SalaEspera`
- `Turno`
- `Sistema`

Descripción:
- `Paciente` utiliza `registrarLlegada()` para modelar su ingreso.
- `LlegadaPaciente` valida la existencia del turno con `validarTurnoExistente(...)` y notifica ingreso a `SalaEspera`.
- `SalaEspera` organiza la fila de pacientes y registra su estado.
- `Turno` puede transitar a `EnEspera`, lo que permite sincronizar la llegada con la atención médica.

## CU4 - Registrar Paciente
Clases principales:
- `Secretaria`
- `Sistema`
- `Paciente`
- `Usuario`

Descripción:
- `Secretaria` inicia el flujo con `solicitarDatosPersonales()` y valida la información con `validarDatos(...)`.
- `Sistema` orquesta el registro mediante `seleccionarRegistrarPaciente()`, `validarDuplicidad(dni)` y `registrarPaciente(datosPersonales)`.
- `Sistema` también crea la cuenta de acceso con `crearCuentaUsuario(datos)`, retornando un `Usuario` asociado al nuevo `Paciente`.
- `Paciente` es el resultado del proceso y concentra los datos de identidad y clínicos del nuevo usuario del sistema.

## CU5 - Ver Agenda
Clases principales:
- `Doctor`
- `Agenda`
- `Turno`
- `Sistema`

Descripción:
- `Doctor` consulta su agenda con `verAgenda(fecha: LocalDate)`, que retorna `List<Turno>`.
- `Agenda` representa la programación diaria del doctor y expone métodos como `obtenerTurnosDelDia(...)`, `crearAgendaDelDia(...)` y `validarTurnosContraReglas()`.
- `Turno` y `Especialidad` permiten ver qué citas están asociadas a cada especialidad y horario.
- `Sistema` orquesta la consulta con `seleccionarVerAgenda()` y permite al doctor consultar un paciente específico con `consultarPacienteEspecifico(turno)`.

## Referencias de contexto
Este análisis se construyó a partir de:
- `herramientas-agile/tarjetas-crc/`
- `diagramas/01-diagrama-clases/06-clases-diagrama-final.puml`
- `diagramas/05-diagramas-secuencia/`