# Reporte de IA - Documentador y Coordinador (A3)

Este documento registra el proceso de auditoría y revisión de código (Code Review) asistido por IA para asegurar la calidad de la Actividad N3.

---

## 1. Supervisión: Especialista en Actividades (CU 1 y 2)
**Responsable:** Caterina Cerdán

### Revisión de PR #[87]
- **Prompt utilizado:** 

```
Actuá como un Ingeniero de Software Senior y Arquitecto de Soluciones. Estoy realizando la Code Review de la especialidad de Diagramas de Actividades (Casos de Uso 1 y 2) para nuestro Sistema de Turnos Médicos. 

Analizá los cambios introducidos en #87 (vinculada a las issues #85 y #86).

Objetivo: Evaluar la coherencia lógica, la consistencia arquitectónica y el cumplimiento de las reglas de negocio de los nuevos diagramas de actividades frente a los artefactos preexistentes del proyecto.

Instrucciones de Auditoría de Consistencia (Cruce de Datos):

1. Coherencia con Tarjetas CRC y Clases:
Compará las acciones de los carriles (swimlanes) que están en los archivos modificados de esta PR con nuestras Tarjetas CRC de la entrega anterior. ¿Los métodos invocados en el Sistema (ej. verificarDisponibilidad(), registrarTurno()) y las interacciones de los actores existen y coinciden con las responsabilidades ya asignadas a las clases Paciente, Secretaria, Médico o SistemaTurnosMédicos?

2. Fidelidad con Escenarios de Casos de Uso:
Cruzá el flujo del diagrama de actividades de la PR con los archivos de escenarios correspondientes de la entrega previa (Flujo Principal y Flujos Alternativos en la carpeta diagramas/03-escenarios-casos-de-uso/). ¿El diagrama de actividades refleja fielmente los pasos del escenario? ¿Se mapearon correctamente las precondiciones, postcondiciones y las excepciones del negocio (ej. si no hay turnos disponibles)?

3. Estructura y Reglas UML Técnicas:
- Validá que cada diagrama modificado cuente con al menos 10 actividades lógicas y conectadas, sin saltos abruptos.
- Verificá que existan al menos 3 carriles (swimlanes) distribuyendo las responsabilidades de forma correcta.
- Analizá los nodos de decisión (rombos): ¿Tienen los caminos alternativos claramente etiquetados con condiciones mutuamente excluyentes (ej. [Si hay cupo] / [No hay cupo])? ¿Tienen un único inicio y fin válidos?

4. Sintaxis y Formato:
¿El código PlantUML (.puml) de la PR compila de forma limpia y mantiene una nomenclatura profesional en español acorde al resto del repositorio?

---
Resultado esperado:
Por favor, presentá tu reporte técnico estructurado en:
- Análisis de Coherencia y Consistencia (Detallando si respeta las CRC y los escenarios previos).
- Deficiencias Lógicas o Errores Técnicos de UML Encontrados.
- Veredicto de Integración (APROBAR o SOLICITAR CAMBIOS "Request Changes" detallando el porqué arquitectónico).
```
- **Output de Copilot:** 
La IA emitió un veredicto de "REQUEST CHANGES" tras un análisis cruzado con las Tarjetas CRC y los Escenarios de la A2. Si bien validó que los diagramas cumplen con los mínimos técnicos (15 y 16 actividades, y 3/4 swimlanes), detectó 3 inconsistencias de diseño:
  * En CU2, el "Médico" recibe una notificación de forma directa en su carril, violando el principio de que el "Sistema" debe ser el orquestador y omitiendo que la CRC del Médico no posee esa responsabilidad.
  * En CU1, falta validar la precondición obligatoria del escenario: verificar si el paciente está registrado antes de mostrar la disponibilidad.
  * Ambigüedad en el flujo de error de credenciales, donde se indica "Reintentar" pero el flujo corta inmediatamente con un "stop".

- **Ajustes y Correcciones aplicadas:**
  1. *Filtro de Bloqueos:* Adopté las observaciones 1 y 2 como cambios obligatorios (bloqueantes) debido a su impacto en la consistencia del modelo dinámico con el estático (CRC).
  2. *Suavizado de Criterio:* Clasifiqué la observación sobre el reintento de credenciales (punto 3) y el carril pasivo del médico como "Recomendaciones de diseño opcionales" para no sobrecargar el retrabajo de la especialista, priorizando la entrega a tiempo.
  3. *Acción:* Publiqué la solicitud de cambios en GitHub detallando las correcciones de código PlantUML sugeridas por la IA.

---

## 2. Supervisión: Especialista en Actividades (CU 3, 4 y 5)
**Responsable:** Facundo Guiraldes

### Revisión de PR #[88]
- **Prompt utilizado:** 

```
Actuá como un Ingeniero de Software Senior y Arquitecto de Soluciones. Estoy realizando la Code Review de la especialidad de Diagramas de Actividades (Casos de Uso 3, 4 y 5) para nuestro Sistema de Turnos Médicos. 

Analizá los archivos modificados en la PR #88 (vinculada a las issues #90, #91 y #92).

Objetivo: Evaluar la coherencia lógica, la consistencia arquitectónica y el cumplimiento estricto de las reglas de negocio de los nuevos diagramas de actividades frente a las Tarjetas CRC y los Escenarios preexistentes del proyecto.

Instrucciones de Auditoría de Consistencia (Cruce de Datos en GitHub Web):

1. Coherencia con Tarjetas CRC y Clases:
Compará las acciones de los carriles (swimlanes) presentes en los nuevos archivos .puml de esta PR con nuestras Tarjetas CRC de la entrega anterior. ¿Los métodos invocados en el Sistema y las interacciones de los actores existen y coinciden con las responsabilidades ya asignadas a las clases del modelo estático (Paciente, Secretaria, Médico, SistemaTurnosMédicos, etc.)?

2. Fidelidad con Escenarios de Casos de Uso (A2):
Cruzá el flujo de cada uno de los tres diagramas de actividades con sus respectivos archivos de escenarios de la entrega previa ubicados en la carpeta `diagramas/03-escenarios-casos-de-uso/`. ¿Cada diagrama de actividades refleja fielmente el Flujo Principal y los Flujos Alternativos de su escenario correspondiente? ¿Se mapearon correctamente las precondiciones, postcondiciones y excepciones del negocio?

3. Estructura y Reglas UML Técnicas (Rúbrica de Puntos):
- Validá que CADA UNO de los 3 diagramas cuente con al menos 10 actividades lógicas, descriptivas y conectadas, sin saltos abruptos.
- Verificá que existan al menos 3 carriles (swimlanes) por diagrama, distribuyendo correctamente las responsabilidades según los actores involucrados (ej. si es sobreturno, el Médico debe ser central; si es recepción, la Secretaria, etc.).
- Analizá los nodos de decisión (rombos): ¿Tienen los caminos alternativos condiciones mutuamente excluyentes? ¿Tienen un único nodo de inicio y terminan en un fin (stop) válido?

4. Sintaxis, Nomenclatura e Índice:
- ¿El código PlantUML (.puml) de los tres archivos compila de forma limpia y mantiene una nomenclatura profesional en español acorde al resto del repositorio?
- ¿Se actualizaron correctamente los archivos .png secuenciales y se registró todo en el índice `diagramas/04-diagramas-actividades/diagramas_de_actividades.md`?

---
Resultado esperado:
Por favor, presentá tu reporte técnico estructurado en:
- Análisis de Coherencia y Consistencia (Detallando si respeta las CRC y los escenarios de los CU 3, 4 y 5).
- Deficiencias Lógicas o Errores Técnicos de UML Encontrados (Indicar archivo y línea si es posible).
- Veredicto de Integración (APROBAR o SOLICITAR CAMBIOS "Request Changes" detallando el porqué arquitectónico).
```

- **Output de Copilot:** La IA arrojó inicialmente un veredicto de "SOLICITAR CAMBIOS" debido a un fallo de flujo en el CU05 (Ver Agenda). Validó de forma excelente que los tres diagramas cumplen con la estructura estricta (13, 15 y 16 actividades respectivamente, cumpliendo el mínimo de 10) y la distribución en 3 swimlanes. Sin embargo, detectó que en el CU05, ante un error de credenciales, el flujo indica un reingreso pero finaliza inmediatamente con un nodo 'stop' inválido para un ciclo continuo.
- **Ajustes y Correcciones aplicadas:**
  1. *Suavizado de Veredicto:* Cambié el dictamen de "Request Changes" a "APPROVE" (Aprobación con observaciones). El defecto en el CU05 es menor/conceptual y no compromete la lógica macro del sistema. Prioricé avanzar con el merge para mantener la fluidez del equipo.
  2. *Filtrado de Retrabajo:* La observación del CU05 se le comunicó al especialista como una sugerencia de mejora de diseño opcional, permitiendo que la PR se integre de inmediato a develop.
  3. *Acción:* Merge de la PR #88 aprobado en GitHub.
    
---

## 3. Supervisión: Especialista en Secuencia
**Responsable:** Valeria Silva

### Revisión de PR #[84]
- **Prompt utilizado:** 

```
Actuá como un Ingeniero de Software Senior y Arquitecto de Soluciones. Estoy realizando la Code Review de la especialidad de Diagramas de Secuencia para nuestro Sistema de Turnos Médicos. 

Analizá los archivos modificados en la PR #84 (vinculada a las issues #79, #80, #81, #82 y #83).

Objetivo: Evaluar la consistencia temporal, el rigor técnico de la notación UML y el cumplimiento estricto de los requisitos de diseño interactivo frente a las Tarjetas CRC y los Escenarios de la entrega previa.

Instrucciones de Auditoría de Consistencia (Cruce de Datos en GitHub Web):

1. Estructura de Participantes y Notación UML (Rúbrica de Puntos):
- Validá que CADA UNO de los 5 diagramas incluya al menos 4 participantes (actores u objetos del sistema).
- Verificá que el primer participante a la izquierda sea el actor que inicia el escenario (Paciente, Secretaria, Médico o interfaz como PantallaTurnos).
- Revisá la nomenclatura de los participantes: ¿Cumple con la notación formal UML para distinguir clases (Clase), objetos (:objeto) o instancias específicas (objeto:Clase)?
- Identificá si existen objetos temporales (ej. un controlador de sesión, un token de validación o un objeto de notificación interna) y validá que se indique su finalización mediante la destrucción explícitamente de la línea de vida con un "destroy" (la cruz "X").

2. Flujo de Mensajes, Naming y Firmas de Métodos:
- Verificá que cada participante cuente con un mínimo de 3 mensajes o interacciones con otros componentes.
- Validá que todos los mensajes entre objetos sigan un orden cronológico coherente y utilicen la nomenclatura camelCase.
- Controlá que los mensajes incluyan sus argumentos o parámetros necesarios (ej. enviarNotificacion(paciente, mensaje)) en lugar de ser texto plano descriptivo.

3. Fidelidad con Artefactos Previos (Escenarios A2 y Tarjetas CRC):
- Cruzá los diagramas con los escenarios de `diagramas/03-escenarios-casos-de-uso/` y las Tarjetas CRC en `herramientas-agile/tarjetas-crc/`. ¿El orden de las llamadas refleja el flujo principal/alternativo del escenario? ¿Los objetos receptores de los mensajes coinciden con las clases que tienen asignadas esas responsabilidades en las Tarjetas CRC?

4. Entregables e Índices del Repositorio:
- ¿El código PlantUML (.puml) de los 5 archivos compila de manera limpia y sin errores de sintaxis?
- ¿Se generaron los archivos .png secuenciales en la carpeta `diagramas/05-diagramas
```

- **Output de Copilot:** El análisis de la IA otorgó una "Aprobación Condicional" identificando dos bloqueantes críticos: un conflicto de Git en `changelog.md` que impide el merge automático, y la ausencia de la sentencia `destroy` para los objetos temporales (`nuevoPaciente` y `usuario`) en el CU04, lo cual viola un ítem explícito de la rúbrica de evaluación (0.25 pts). También detectó desajustes menores de nomenclatura (uso de `get*` en el CU05) e inconsistencias semánticas leves entre el Sistema y la Agenda.
- **Ajustes y Correcciones aplicadas:**
  1. *Validación de Bloqueantes:* Coincido con la IA. El conflicto de Git y la falta del `destroy` en el CU04 son errores de rúbrica directos que impactan en la nota. Se frena el merge.
  2. *Suavizado de Observaciones Menores:* Las sugerencias de cambiar los métodos `get*` y reestructurar la lógica de la Agenda se pasaron como mejoras opcionales post-merge para no sobrecargar a la especialista.
  3. *Acción:* PR puesta en "Request Changes" hasta que se resuelvan los dos puntos críticos.

---

## 4. Supervisión: 
**Responsable:** 

### Revisión de Integración
- **Prompt utilizado:** 
- **Output de Copilot:** 
- **Ajustes y Correcciones aplicadas:**
    