# Documentación de uso de IA - Modelador de Casos de Uso

## Prompt utilizado
Actúa como un experto en UML y PlantUML en modo Copilot Agent. 
Lee el archivo `anexos/introduccion.md` como contexto.
Genera el código PlantUML para los 5 casos de uso identificados en la Actividad 1 (Solicitar turno, Cancelar turno, Registrar llegada, Registrar paciente, Ver agenda).
Asegúrate de incluir:
- Actores principales y secundarios.
- Relaciones de asociación, inclusión (<<include>>) y extensión (<<extend>>).
- El límite del sistema utilizando un bloque `rectangle "Sistema de Turnos Médicos" { }`.

## Archivos de contexto provistos
* `anexos/introduccion.md` (Para extraer los requisitos y flujos de los casos de uso definidos en la Actividad 1).

## Output generado por la IA y Ajustes manuales

**1. 02-caso-uso-solicitar-turno-01.puml**
*   **Output generado:** Generó la estructura básica de actores y casos de uso. Sin embargo, omitió el límite del sistema (`rectangle`) y modeló erróneamente "Notificar asignación al paciente" como una relación `<<extend>>`.
*   **Ajustes manuales:** Se agregó el bloque `rectangle "Sistema de Turnos Médicos" { }` para delimitar el sistema. Se modificó manualmente la relación de notificación a `<<include>>` (`UC1 ..> UC4 : <<include>>`) ya que es una regla obligatoria del dominio.

**2. 02-caso-uso-cancelar-turno-02.puml**
*   **Output generado:** Identificó correctamente las inclusiones de búsqueda y liberación de turno, pero falló en la obligatoriedad de la notificación y omitió el límite del sistema.
*   **Ajustes manuales:** Se envolvió el diagrama en el bloque `rectangle`. Se corrigió la relación "Notificar cancelación" cambiándola de `<<extend>>` a `<<include>>` para cumplir con las reglas del negocio.

**3. 02-caso-uso-registrar-llegada-03.puml**
*   **Output generado:** Omitió por completo al actor "Doctor" en el código PlantUML e intentó aislar el caso de uso "Ver lista de espera". Omitió el `rectangle`.
*   **Ajustes manuales:** Se agregó el límite del sistema (`rectangle`). Se reintegró manualmente al actor Doctor y se lo vinculó agregando una relación `<<extend>>` hacia el flujo central de registro para respetar la postcondición.

**4. 02-caso-uso-registrar-paciente-04.puml**
*   **Output generado:** El código generado estaba incompleto (faltaba la etiqueta de cierre `@enduml`) e inventó un caso de uso fuera de alcance. Omitió el `rectangle`.
*   **Ajustes manuales:** Se agregó la etiqueta de cierre `@enduml`. Se eliminaron los casos de uso fantasma inventados por la IA, se corrigieron las asociaciones de los actores y se agregó el `rectangle`.

**5. 02-caso-uso-ver-agenda-05.puml**
*   **Output generado:** Generó los actores correctamente pero omitió la funcionalidad de "Bloquear horario" requerida en la introducción. Omitió el `rectangle`.
*   **Ajustes manuales:** Se agregó el límite del sistema (`rectangle`). Se insertó manualmente el caso de uso "Bloquear horario" y se lo relacionó con un `<<extend>>` hacia "Ver agenda".

## Iteraciones
El proceso requirió un total de **3 iteraciones**:
1. **Iteración 1:** Generación inicial del código PlantUML crudo para los 5 diagramas mediante Copilot Agent Mode.
2. **Iteración 2:** Revisión contra `anexos/introduccion.md` para reintegrar al actor Doctor, borrar casos de uso alucinados y arreglar la sintaxis de PlantUML.
3. **Iteración 3 (Post-Code Review):** Ajuste manual profundo tras el Request Change del docente para envolver todos los diagramas en el `rectangle` y cambiar la semántica de las notificaciones a `<<include>>`.