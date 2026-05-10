# A2 - Especialista en Escenarios de Casos de Uso

## Descripción de la Tarea
Se desarrollaron escenarios de casos de uso para el sistema de gestión de turnos médicos, utilizando Copilot Agent Mode como asistencia. Se seleccionaron 5 casos de uso relevantes y se generaron escenarios completos siguiendo la plantilla proporcionada.

---

## Prompt Utilizado

```text
Quiero que leas anexos/introducción.md y tengo una plantilla de escenarios para que me puedas completar en cada campo de escenarios con los 5 casos de uso más relevantes (se copió y pegó la plantilla).
```
---

## Archivos Referenciados

- anexos/introduccion.md
- Plantilla de escenarios de casos de uso (formato markdown proporcionado por la cátedra)

---

## Output de la IA por escenario
1. Solicitar turno

La IA generó un escenario con selección de fecha y horario, validación de disponibilidad y confirmación del turno.

2. Cancelar turno

La IA generó un flujo donde el usuario selecciona un turno existente y lo cancela, incluyendo validación del estado del turno.

3. Registrar llegada del paciente

La IA generó un escenario de check-in donde el paciente confirma su presencia en el sistema.

4. Registrar paciente

La IA generó un escenario de alta de paciente con ingreso de datos personales y validación de información.

5. Ver agenda

La IA generó un escenario de consulta de disponibilidad de turnos del profesional.

---

## Escenarios Generados

Se desarrollaron los siguientes escenarios:

- Solicitar turno
- Cancelación de turno
- Registro de llegada del paciente
- Registro de paciente
- Visualización de agenda

---

## Ajustes Realizados al Output

### 1. Solicitar turno
- Se agregaron los requisitos funcionales: RF1 Gestión de turnos, RF3 Notificación automática al paciente, RNF1 Evitar superposición de turnos.
- Se agregaron precondiciones faltantes.

### 2. Cancelar turno
- Se agregaron los requisitos funcionales: RF1 Gestión de turnos, RF3 Notificación automática al paciente, RNF4 Historial de modificaciones.

### 3. Registrar llegada del paciente
- Se ajustó la prioridad a alta y el riesgo a medio.
- Se agregaron los requisitos funcionales: RF5 Check de asistencia, RNF4 Historial de modificaciones.
- Se corrigió la precondición.

### 4. Registrar paciente
- Se agregaron los requisitos: RF1 Gestión de turnos (como precondición), RNF2 Simplicidad.

### 5. Ver agenda
- Se ajustó la prioridad a alta.
- Se agregaron los requisitos: RF2 Visualizar agenda, RF4 Gestión de disponibilidad y bloqueo.
---
## Iteraciones realizadas

Se realizaron 2 iteraciones:

- Generación inicial de escenarios utilizando IA.
- Revisión y corrección manual para ajustar precondiciones, flujo principal, requerimientos y prioridades según la consigna.

## Conclusión

El uso de Copilot permitió agilizar la generación inicial de los escenarios, pero fue necesario realizar una revisión crítica para garantizar que los mismos cumplieran con los requisitos de la consigna y representaran correctamente el funcionamiento del sistema.