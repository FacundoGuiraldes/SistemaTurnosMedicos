# Escenario de Caso de Uso: Solicitar Turno

## Datos generales

- **Nombre del escenario:** Flujo principal - Solicitud de turnos exitoso
- **Nombre del caso de uso:** Solicitar turno
- **ID única:** 1
- **Área:** Sistema de Turnos Médicos, Gestión de Turnos
- **Actor(es):** Paciente, Secretaria
- **Descripción:** Permite al paciente solicitar un turno médico en una fecha y horario disponibles mediante la secretaria.
- **Activar Evento:** El paciente se comunica con la recepción o por teléfono para pedir un turno.

## Identificadores e iniciadores

- **Tipo de señal:** ☑️ Externa  ☐ Temporal

## Pasos del flujo principal

1. El paciente se comunica a la recepción o llama por teléfono.
2. La secretaria ingresa al sistema.
3. El sistema muestra los horarios y fechas disponibles.
4. El paciente elige una fecha y horario.
5. El sistema registra el turno.

## Información para los pasos

- El paciente proporciona sus datos básicos.
- La secretaria utiliza su usuario y clave válidos.
- El sistema consulta la disponibilidad en la agenda del médico.
- El turno se guarda en la base de datos de turnos.

## Condiciones, suposiciones y preguntas

- **Precondiciones:** El paciente debe estar registrado en el sistema.
- **Poscondiciones:** El turno queda guardado en la agenda del sistema y bloquea la disponibilidad en esa franja horaria.
- **Suposiciones:** El paciente puede comunicarse por teléfono o presencial. Hay disponibilidad de turnos.
- **Reunir requerimentos:** RF1 Gestión de turnos
- **Aspectos sobresalientes:** ¿Se notifica automáticamente al paciente por WhatsApp? ¿Qué ocurre si no hay disponibilidad? ¿Se permite sobreturno manual?
- **Prioridad:** Alta
- **Riesgo:** Medio
