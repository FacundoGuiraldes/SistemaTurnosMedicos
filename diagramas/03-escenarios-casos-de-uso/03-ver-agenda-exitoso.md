| **Nombre del escenario:** |Flujo principal - Ver agenda exitoso | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** | Ver agenda | | **ID Única:** | 5 |
| **Área** | Sistema de Turnos Médicos, Visualización de Agenda | | | |
| **Actor(es):** | Doctor | | | |
| **Descripción:** | Permite al doctor visualizar su agenda con los turnos programados de un día determinado. | | | |

| **Activar Evento:** | El doctor accede al sistema y selecciona la opción de ver la agenda. | **Identificadores e iniciadores de caso de uso** |
|---|---|---|
| **Tipo de señal:** | ☑️ Externa | ☐ Temporal | |

| **Pasos desempeñados (ruta principal)** | **Información para los pasos** |
|---|---|
| 1. El doctor accede al sistema. | El doctor ingresa con credenciales válidas. |
| 2. El sistema muestra el menú de opciones disponibles. | El sistema ofrece un calendario o selector de fecha. |
| 3. El doctor selecciona la opción “Ver agenda”. | El doctor elige un día específico. |
| 4. El doctor selecciona el día que desea consultar. | El sistema despliega la agenda completa de ese día. |
| 5. El sistema muestra la agenda con los turnos, pacientes y horarios correspondientes. | La agenda incluye información relevante como nombre del paciente, hora del turno y motivo de consulta. |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | Deben existir turnos asignados en la agenda. |
| **Poscondiciones:** | El doctor puede visualizar los turnos programados. |
| **Suposiciones:** | El doctor tiene credenciales válidas y la agenda está actualizada. |
| **Reunir requerimentos:** | RF2 Visualizar agenda, RF4 Gestión de disponibilidad y bloqueo. |
| **Aspectos sobresalientes:** | ¿Se puede filtrar por semana o mes? ¿Se exporta o imprime la agenda? ¿El doctor puede ver solo sus turnos? |
| **Prioridad:** | Alta |
| **Riesgo:** | Bajo |

