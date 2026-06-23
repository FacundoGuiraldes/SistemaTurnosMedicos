# Análisis Funcional por Casos de Uso

* [Analisis Funcional - Solicitar turno 01](01-caso-de-uso-solicitar-turno.md)
* [Analisis Funcional - Cancelar turno 02](02-caso-de-uso-cancelar-turno.md)
* [Analisis Funcional - Registrar llegada del paciente 03](03-caso-de-uso-registrar-llegada.md)
* [Analisis Funcional - Registrar paciente 04](04-caso-de-uso-registrar-paciente.md)
* [Analisis Funcional - Ver agenda 05](05-caso-de-uso-ver-agenda.md)
* [Los Cuatro Pilares del Paradigma Orientado a Objetos](pilares-poo.md)
* [Pseudocódigo - Happy Path Global del Sistema](happy-path-global.md)

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