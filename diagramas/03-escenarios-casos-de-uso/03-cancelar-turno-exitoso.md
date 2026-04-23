| **Nombre del escenario:** |Flujo principal - cancelar turno exitoso | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** | Cancelar turno | | **ID Única:** | 2 |
| **Área** | Sistema de Turnos Médicos, Gestión de Turnos | | | |
| **Actor(es):** | Paciente, Secretaria | | | |
| **Descripción:** | El paciente se comunica con la secretaria y solicita la cancelación del turno. | | | |

| **Activar Evento:** | El paciente llega al consultorio y notifica su arribo a la secretaria. | **Identificadores e iniciadores de caso de uso** |
|---|---|---|
| **Tipo de señal:** | ☑️ Externa | ☐ Temporal | |

| **Pasos desempeñados (ruta principal)** | **Información para los pasos** |
|---|---|
| 1. El paciente se comunica con la secretaria. | El paciente proporciona su identificación. |
| 2. El paciente solicita cancelar su turno. | La secretaria accede a la agenda. |
| 3. El sistema muestra los turnos activos del paciente. | El sistema lista los turnos asignados al paciente. |
| 4. El paciente indica el turno que desea cancelar. | El turno se elimina o se marca como cancelado en la base de datos. |
| 5. El sistema cancela el turno y libera la disponibilidad. | El paciente recibe una confirmación de cancelación. |
| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | El paciente debe tener un turno asignado. |
| **Poscondiciones:** | El turno queda disponible nuevamente para otra persona. |
| **Suposiciones:** | El paciente recuerda el turno y la cancelación se realiza con la debida antelación. |
| **Reunir requerimentos:** | RF1 Gestión de turnos, RF3 Notificación automática al paciente, RNF4 Historial de modificaciones. |
| **Aspectos sobresalientes:** | ¿Se notifica al paciente y al médico? ¿Se permite cancelación tardía? ¿Se registra el motivo de la cancelación? |
| **Prioridad:** | Alta |
| **Riesgo:** | Medio |
