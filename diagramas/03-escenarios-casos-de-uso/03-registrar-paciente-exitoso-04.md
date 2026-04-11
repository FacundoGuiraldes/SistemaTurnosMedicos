# Escenario de Caso de Uso: Registrar al paciente

## Datos generales

- **Nombre del escenario:** Flujo principal - Registro de paciente exitoso
- **Nombre del caso de uso:** Registrar al paciente
- **ID única:** 4
- **Área:** Sistema de Turnos Médicos, Gestión de Pacientes
- **Actor(es):** Paciente, Secretaria
- **Descripción:** Permite guardar los datos personales del paciente en el sistema para que pueda solicitar turnos.
- **Activar Evento:** El paciente se presenta en el consultorio o se comunica telefónicamente con la secretaria que realiza el registro.

## Identificadores e iniciadores

- **Tipo de señal:** ☑️ Externa  ☐ Temporal

## Pasos del flujo principal

1. El paciente se presenta en el consultorio o llama por teléfono.
2. La secretaria solicita los datos personales del paciente.
3. El paciente proporciona la información requerida.
4. La secretaria ingresa los datos en el sistema.
5. El sistema registra y almacena los datos del paciente.

## Información para los pasos

- Se recopilan datos como nombre, documento, teléfono y dirección.
- La secretaria valida la información proporcionada.
- El sistema verifica si el paciente ya existe en la base de datos.
- El registro se guarda y el paciente queda habilitado para pedir turnos.

## Condiciones, suposiciones y preguntas

- **Precondiciones:** El paciente debe otorgar sus datos personales.
- **Poscondiciones:** El paciente puede solicitar turnos en el sistema.
- **Suposiciones:** El paciente tiene sus datos completos y la secretaria dispone de acceso al sistema.
- **Reunir requerimentos:** RF1 Gestión de turnos
- **Aspectos sobresalientes:** ¿Se valida la duplicidad del paciente? ¿Se guarda historial médico básico? ¿Se requiere consentimiento para datos sensibles?
- **Prioridad:** Alta
- **Riesgo:** Medio
