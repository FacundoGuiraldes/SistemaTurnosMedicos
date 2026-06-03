# Documentación de Copilot Agent Mode Especialista en Diagramas de Actividades - Caso de Uso 1 y 2

## Prompts utilizados

```text
Necesito que generes un diagrama de actividades en PlantUML para el Caso de Uso 1.

IMPORTANTE:
Usar como contexto los siguientes archivos del proyecto antes de generar el diagrama:

diagramas/02-casos-de-uso/02-caso-uso-solicitar-turno-01
diagramas/03-escenarios-casos-de-uso/03-solicitar-turno-exitoso.md
REQUISITOS OBLIGATORIOS DEL DIAGRAMA:

Debe estar realizado en PlantUML.
Debe incluir mínimo 10 actividades.
Debe incluir mínimo 3 swimlanes/carriles.
Los carriles deben reflejar responsabilidades reales de los actores/componentes.
Debe incluir:
nodo de inicio
nodo de fin
decisiones (if/else)
caminos alternativos
flujo lógico claro
Los nombres deben ser consistentes con los casos de uso y escenarios previos.
El flujo debe reflejar fielmente el escenario principal documentado.
Usar nombres descriptivos para las actividades.
El diagrama debe verse profesional y ordenado.
Carriles sugeridos:

Paciente
Secretaria
SistemaTurnosMedicos
Médico
```
## Output obtenido

GitHub Copilot generó un diagrama de actividades inicial para el caso de uso “Solicitar turno exitoso”, contemplando los carriles Paciente, Secretaria, SistemaTurnosMedicos y Médico.

El flujo generado incluía:

- inicio de la solicitud del turno por parte del paciente,
- validación de credenciales de la secretaria,
- revisión de agenda médica,
- visualización de horarios disponibles,
- selección de fecha y horario,
- validación de disponibilidad,
- registro del turno,
- actualización de disponibilidad,
- envío de notificación al paciente,
- caminos alternativos para credenciales inválidas y falta de disponibilidad.

El output también incorporó estructuras condicionales (if/else) y caminos alternativos para reintentos de selección de horarios.

## Ajustes realizados al Output

Se corrigió la ubicación de actividades dentro de los swimlanes para representar correctamente las responsabilidades de cada actor.

- Se movió la actividad “Informar que no hay disponibilidad” desde el carril Paciente hacia Secretaria.
- Se movió la decisión “Paciente confirma datos” al carril Secretaria, ya que la interacción es gestionada por dicho actor en el escenario definido.
- Se corrigió el flujo de decisiones asociado a “Credenciales válidas”, ajustando la lógica del camino sí/no.
- Se reorganizaron caminos alternativos para evitar conexiones inconsistentes entre actividades y finales del flujo.
- Se simplificaron algunos recorridos alternativos para mantener coherencia con el escenario principal definido en A2.
- Se revisó manualmente la sintaxis PlantUML para corregir errores de renderizado y mejorar la visualización general del diagrama.
- Se realizaron iteraciones adicionales para mejorar:
    * claridad visual,
    * distribución de responsabilidades,
    * coherencia lógica,
    * trazabilidad con escenarios y casos de uso previos.

---

## Prompts utilizados

```text
Necesito que generes un diagrama de actividades en PlantUML para el Caso de Uso 2.

IMPORTANTE:
Usar como contexto los siguientes archivos del proyecto antes de generar el diagrama:

diagramas/02-casos-de-uso/02-caso-uso-cancelar-turno-02
diagramas/03-escenarios-casos-de-uso/03-cancelar-turno-exitoso.md
REQUISITOS OBLIGATORIOS DEL DIAGRAMA:

Debe estar realizado en PlantUML.
Debe incluir mínimo 10 actividades.
Debe incluir mínimo 3 swimlanes/carriles.
Los carriles deben reflejar responsabilidades reales de los actores/componentes.
Debe incluir:
nodo de inicio
nodo de fin
decisiones (if/else)
caminos alternativos
flujo lógico claro
Los nombres deben ser consistentes con los casos de uso y escenarios previos.
El flujo debe reflejar fielmente el escenario principal documentado.
Usar nombres descriptivos para las actividades.
El diagrama debe verse profesional y ordenado.
Carriles sugeridos:

Paciente
Secretaria
SistemaTurnosMedicos
Médico
```
## Output obtenido

GitHub Copilot generó un diagrama de actividades inicial para el caso de uso “Cancelar turno exitoso”, contemplando los carriles Paciente, Secretaria, SistemaTurnosMedicos y Médico.

El flujo generado incluía:

- inicio de la solicitud de cancelación por parte del paciente,
- ingreso de identificación del paciente,
- inicio de sesión de la secretaria,
- validación de credenciales,
- consulta de turnos activos,
- selección del turno a cancelar,
- validación de existencia del turno,
- cancelación del turno en la agenda,
- liberación de la franja horaria,
- actualización del estado del turno,
- registro del cambio en el historial,
- notificación al paciente,
- notificación al médico,
- caminos alternativos para credenciales inválidas y turno no encontrado.

El output también incorporó decisiones para validar credenciales y verificar si existía un turno activo asociado al paciente.

## Ajustes realizados al Output

- Se corrigió el flujo de credenciales inválidas para que, luego de “Mostrar error de inicio de sesión” y “Reintentar con credenciales válidas o contactar soporte”, el proceso finalice correctamente.
- Se movió la decisión “¿Turno encontrado?” desde el carril Paciente hacia el carril Secretaria, ya que la secretaria es quien verifica y gestiona la información del turno.
- Se reorganizó el flujo cuando no existe un turno activo: “Informar que no hay un turno activo para ese paciente” quedó en el carril Secretaria.
- Luego se agregó “Finalizar atención sin cancelar turno”. El flujo termina allí, sin recorridos innecesarios.
- Se movió la actividad “Notificar cancelación al paciente” desde SistemaTurnosMedicos hacia Secretaria, porque la comunicación con el paciente es gestionada por la secretaria.
- Se mantuvieron en SistemaTurnosMedicos las actividades propias del sistema:
    - cancelar turno en la agenda,
    - liberar disponibilidad de la franja horaria,
    - actualizar estado del turno como cancelado,
    - registrar cambio en historial de modificaciones.
- Se dejó en el carril Médico la notificación correspondiente sobre la cancelación del turno.
- Se corrigieron conexiones entre decisiones, actividades y finales para evitar caminos confusos o innecesarios.
Se revisó manualmente la sintaxis PlantUML para asegurar que el diagrama se genere correctamente.