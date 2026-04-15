# Escenario de Caso de Uso: Ver agenda

## Datos generales

- **Nombre del escenario:** Flujo principal - Ver agenda exitoso
- **Nombre del caso de uso:** Ver agenda
- **ID única:** 5
- **Área:** Sistema de Turnos Médicos, Visualización de Agenda
- **Actor(es):** Doctor
- **Descripción:** Permite al doctor visualizar su agenda con los turnos programados de un día determinado.
- **Activar Evento:** El doctor accede al sistema y selecciona la opción de ver la agenda.

## Identificadores e iniciadores

- **Tipo de señal:** ☑️ Externa  ☐ Temporal

## Pasos del flujo principal

1. El doctor accede al sistema.
2. El sistema muestra el menú de opciones disponibles.
3. El doctor selecciona la opción “Ver agenda”.
4. El doctor selecciona el día que desea consultar.
5. El sistema muestra la agenda con los turnos, pacientes y horarios correspondientes.

## Información para los pasos

- El doctor ingresa con credenciales válidas.
- El sistema ofrece un calendario o selector de fechas.
- El doctor elige un día específico.
- El sistema despliega la agenda completa de ese día.

## Condiciones, suposiciones y preguntas

- **Precondiciones:** Deben existir turnos asignados en la agenda.
- **Poscondiciones:** El doctor puede visualizar los turnos programados.
- **Suposiciones:** El doctor tiene credenciales válidas y la agenda está actualizada.
- **Reunir requerimentos:** RF2 Visualizar agenda, RF4 Gestión de disponibilidad y bloqueo.
- **Aspectos sobresalientes:** ¿Se puede filtrar por semana o mes? ¿Se exporta o imprime la agenda? ¿El doctor puede ver solo sus turnos?
- **Prioridad:** Alta
- **Riesgo:** Bajo
