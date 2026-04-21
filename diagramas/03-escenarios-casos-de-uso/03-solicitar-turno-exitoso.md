| **Nombre del escenario:** |Flujo principal - Solicitar turno exitoso | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** | Solicitar turno | | **ID Única:** | 1 |
| **Área** | Sistema de Turnos Médicos, Gestión de Turnos | | | |
| **Actor(es):** | Paciente, Secretaria | | | |
| **Descripción:** | Permite al paciente solicitar un turno médico en una fecha y horario disponibles mediante la secretaria. | | | |

| **Activar Evento:** | El paciente se comunica con la recepción o por teléfono para pedir un turno. | **Identificadores e iniciadores de caso de uso** |
|---|---|---|
| **Tipo de señal:** | ☑️ Externa | ☐ Temporal | |

| **Pasos desempeñados (ruta principal)** | **Información para los pasos** |
|---|---|
| 1. El paciente se comunica a la recepción o llama por teléfono. | El paciente proporciona sus datos básicos. |
| 2. La secretaria ingresa al sistema. | La secretaria utiliza su usuario y clave válidos. |
| 3. El sistema muestra los horarios y fechas disponibles. | El sistema consulta la base de datos de turnos para mostrar la disponibilidad. |
| 4. El paciente elige una fecha y horario. | El paciente selecciona una fecha y horario que se muestra como disponible. |
| 5. El sistema registra el turno. | El sistema guarda el turno asignado al paciente en la base de datos. |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | El paciente debe estar registrado en el sistema. Deben existir fechas y horarios disponibles en la agenda del médico. |
| **Poscondiciones:** | El turno queda guardado en la agenda del sistema y bloquea la disponibilidad en esa franja horaria. |
| **Suposiciones:** | El paciente puede comunicarse por teléfono o presencial. Hay disponibilidad de turnos. |
| **Reunir requerimentos:** | RF1 Gestión de turnos, RF3 Notificación automática al paciente, RNF1 Evitar superposición de turnos. |
| **Aspectos sobresalientes:** | ¿Se notifica automáticamente al paciente por WhatsApp? ¿Qué ocurre si no hay disponibilidad? ¿Se permite sobreturno manual? |
| **Prioridad:** | Alta |
| **Riesgo:** | Medio |
