| **Nombre del escenario:** |Flujo principal - Registrar paciente exitoso | | | |
|---|---|---|---|---|
| **Nombre del caso de uso:** | Registrar paciente | | **ID Única:** | 4 |
| **Área** | Sistema de Turnos Médicos, Gestión de Pacientes | | | |
| **Actor(es):** | Paciente, Secretaria | | | |
| **Descripción:** | Permite guardar los datos personales del paciente en el sistema para que pueda solicitar turnos. | | | |

| **Activar Evento:** | El paciente se presenta en el consultorio o se comunica telefónicamente con la secretaria que realiza el registro. | **Identificadores e iniciadores de caso de uso** |
|---|---|---|
| **Tipo de señal:** | ☑️ Externa | ☐ Temporal | |

| **Pasos desempeñados (ruta principal)** | **Información para los pasos** |
|---|---|
| 1. El paciente se presenta en el consultorio o llama por teléfono. | Se recopilan datos como nombre, documento, teléfono y dirección. |
| 2. La secretaria solicita los datos personales del paciente. | La secretaria valida la información proporcionada. |
| 3. El paciente proporciona la información requerida. | El sistema verifica si el paciente ya existe en la base de datos. |
| 4. La secretaria ingresa los datos en el sistema. | El registro se guarda y el paciente queda habilitado para pedir turnos. |
| 5. El sistema registra y almacena los datos del paciente. | El paciente recibe una confirmación de registro exitoso. |

| **Condiciones, suposiciones y preguntas** | |
|---|---|
| **Precondiciones:** | El paciente debe otorgar sus datos personales. |
| **Poscondiciones:** | El paciente puede solicitar turnos en el sistema. |
| **Suposiciones:** | El paciente tiene sus datos completos y la secretaria dispone de acceso al sistema. |
| **Reunir requerimentos:** | RF1 Gestión de turnos (como precondición), RNF2 Simplicidad. |
| **Aspectos sobresalientes:** | ¿Se valida la duplicidad del paciente? ¿Se guarda historial médico básico? ¿Se requiere consentimiento para datos sensibles? |
| **Prioridad:** | Alta |
| **Riesgo:** | Medio |