# Escenario de Caso de Uso: Registrar llegada del paciente

## Datos generales

- **Nombre del escenario:** Flujo principal - Registro de llegada del paciente exitoso
- **Nombre del caso de uso:** Registrar llegada del paciente
- **ID única:** 3
- **Área:** Sistema de Turnos Médicos, Gestión de Asistencia
- **Actor(es):** Paciente, Secretaria, Doctor
- **Descripción:** Permite registrar en el sistema la llegada del paciente al consultorio y el tiempo desde su arribo.
- **Activar Evento:** El paciente llega al consultorio y notifica su arribo a la secretaria.

## Identificadores e iniciadores

- **Tipo de señal:** ☑️ Externa  ☐ Temporal

## Pasos del flujo principal

1. El paciente llega al consultorio.
2. El paciente informa a la secretaria que ha llegado.
3. La secretaria busca el turno del paciente en el sistema.
4. La secretaria registra la llegada del paciente.
5. El sistema marca al paciente como “en espera” y guarda la hora de llegada.

## Información para los pasos

- Se cuenta con el nombre o identificación del paciente.
- La secretaria accede a la agenda del día.
- El sistema actualiza el estado del turno.
- Se registra la hora real de llegada.

## Condiciones, suposiciones y preguntas

- **Precondiciones:** El paciente debe tener un turno asignado para el día actual en el sistema y llegar al lugar del consultorio.
- **Poscondiciones:** El doctor puede ver quién está esperando y desde cuándo.
- **Suposiciones:** El paciente tiene un turno asignado y la secretaria está disponible.
- **Reunir requerimentos:** RF5 Check de asistencia, RNF4 Historial de modificaciones.
- **Aspectos sobresalientes:** ¿Cómo manejar pacientes sin turno? ¿Se registra el motivo de la demora? ¿El paciente puede avisar llegada por WhatsApp?
- **Prioridad:** Alta
- **Riesgo:** Medio
