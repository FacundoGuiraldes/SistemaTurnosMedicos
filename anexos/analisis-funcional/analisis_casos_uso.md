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

## CU4 - Ver Agenda
Clases principales:
- `Doctor`
- `Agenda`
- `Turno`
- `Sistema`

Descripción:
- `Doctor` consulta su agenda con `verAgenda(fecha: LocalDate)`.
- `Agenda` representa la programación diaria del doctor y responde con los turnos asociados.
- `Turno` y `Especialidad` permiten ver qué citas están asociadas a cada especialidad y horario.
- `Sistema` puede orquestar esta consulta para asegurar que el doctor solo acceda a su propia agenda.

## CU5 - Envío de Notificaciones
Clases principales:
- `Sistema`
- `ServicioNotificaciones`
- `Notificacion`
- `Paciente`
- `Turno`

Descripción:
- `Sistema` delega el envío de alertas a `ServicioNotificaciones` con `enviarRecordatorioAutomatico(...)`.
- `ServicioNotificaciones` envía mensajes relacionados con el `Turno` y el estado del paciente.
- La entidad `Notificacion` modela los metadatos asociados al mensaje y su destinatario.

## Referencias de contexto
Este análisis se construyó a partir de:
- `herramientas-agile/tarjetas-crc/`
- `diagramas/01-diagrama-clases/06-clases-diagrama-final.puml`
- `diagramas/05-diagramas-secuencia/`