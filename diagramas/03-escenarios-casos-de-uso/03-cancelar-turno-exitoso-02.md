# Escenario de Caso de Uso: Cancelar Turno

## Datos generales

- **Nombre del escenario:** Flujo principal - Cancelar turno exitoso
- **Nombre del caso de uso:** Cancelar turno
- **ID única:** 2
- **Área:** Sistema de Turnos Médicos, Gestión de Turnos
- **Actor(es):** Paciente, Secretaria
- **Descripción:** Permite al paciente cancelar un turno previamente asignado.
- **Activar Evento:** El paciente se comunica con la secretaria y solicita la cancelación del turno.

## Identificadores e iniciadores

- **Tipo de señal:** ☑️ Externa  ☐ Temporal

## Pasos del flujo principal

1. El paciente se comunica con la secretaria.
2. El paciente solicita cancelar su turno.
3. El sistema muestra los turnos activos del paciente.
4. El paciente indica el turno que desea cancelar.
5. El sistema cancela el turno y libera la disponibilidad.

## Información para los pasos

- El paciente proporciona su identificación.
- La secretaria accede a la agenda.
- El sistema lista los turnos asignados al paciente.
- El turno se elimina o se marca como cancelado en la base de datos.

## Condiciones, suposiciones y preguntas

- **Precondiciones:** El paciente debe tener un turno asignado.
- **Poscondiciones:** El turno queda disponible nuevamente para otra persona.
- **Suposiciones:** El paciente recuerda el turno y la cancelación se realiza con la debida antelación.
- **Reunir requerimentos:** RF1 Gestión de turnos, RF3 Notificación automática al paciente, RNF4 Historial de modificaciones.
- **Aspectos sobresalientes:** ¿Se notifica al paciente y al médico? ¿Se permite cancelación tardía? ¿Se registra el motivo de la cancelación?
- **Prioridad:** Alta
- **Riesgo:** Medio
