# Registro de Proceso de IA - Especialista en Diagramas de Actividades

Este documento registra la interacción con GitHub Copilot para la generación de los diagramas de actividades de los Casos de Uso 3, 4 y 5, garantizando la trazabilidad con los artefactos de la Actividad 2.

---

## Caso de Uso 3: Registrar llegada del paciente

**Prompt utilizado:**
Actúa como un Especialista en UML y Analista Funcional. Debo generar el diagrama de actividades para el Caso de Uso 3: "Registrar llegada del paciente", siguiendo la estructura de la Actividad Obligatoria N°3.

CONTEXTO DE ENTRADA (Referencia obligatoria):
- Basate en el flujo lógico de: diagramas/03-escenarios-casos-de-uso/03-registrar-llegada-del-paciente-exitoso.md
- Basate en los actores de: diagramas/02-casos-de-uso/02-caso-uso-registrar-llegada-03.puml

REQUISITOS TÉCNICOS DE SALIDA:
1. Nomenclatura del archivo: El código debe estar pensado para guardarse como "04-actividad-registrar-llegada-03.puml" dentro de la carpeta "diagramas/04-diagramas-actividades/".
2. Estructura de Carriles (Swimlanes): Crea 3 carriles claramente definidos: |Paciente|, |Sistema| y |Secretaria|.
3. Densidad de Actividades: El diagrama debe tener un mínimo de 10 actividades detalladas (nodos de acción).
4. Trazabilidad: Cada paso del diagrama debe corresponderse con los pasos del flujo principal del archivo .md de la Actividad 2.
5. Lógica de Control: Incluye al menos un rombo de decisión (if/else) para representar la validación de los datos del paciente o la existencia del turno.
6. Sintaxis: Utiliza la sintaxis moderna de PlantUML (!theme, start, stop, :actividad;).

Genera el código PlantUML completo y profesional.


## Caso de Uso 4: Registrar paciente

**Prompt utilizado:**
Actúa como un Especialista en UML y Analista Funcional. Debo generar el diagrama de actividades para el Caso de Uso 4: "Registrar paciente", siguiendo la estructura de la Actividad Obligatoria N°3 y continuando el trabajo de la PR #89.

CONTEXTO DE ENTRADA (Referencia obligatoria):
- Basate en el flujo lógico de: diagramas/03-escenarios-casos-de-uso/03-registrar-paciente-exitoso.md
- Basate en los actores de: diagramas/02-casos-de-uso/02-caso-uso-registrar-paciente-04.puml

REQUISITOS TÉCNICOS DE SALIDA:
1. Nomenclatura del archivo: El código debe estar pensado para guardarse como "04-actividad-registrar-paciente-04.puml" dentro de la carpeta "diagramas/04-diagramas-actividades/".
2. Estructura de Carriles (Swimlanes): Crea 3 carriles claramente definidos: |Paciente|, |Sistema| y |Secretaria|.
3. Densidad de Actividades: El diagrama debe tener un mínimo de 10 actividades detalladas.
4. Trazabilidad: Cada paso del diagrama debe corresponderse con los pasos del flujo principal del escenario exitoso de la Actividad 2.
5. Lógica de Control: Incluye un rombo de decisión (if/else) para representar la validación de los datos.
6. Sintaxis: Utiliza la sintaxis moderna de PlantUML.

Genera el código PlantUML completo para integrar en la PR #89. Esta PR luego se mergeará manualmente a la PR #88 para su review.


## Caso de Uso 5: Ver agenda

**Prompt utilizado:**
Actúa como un Especialista en UML y Analista Funcional Sr. Debo generar el diagrama de actividades para el Caso de Uso 5: "Ver agenda", siguiendo la estructura de la Actividad Obligatoria N°3 y consolidando el trabajo en la PR #89.

CONTEXTO DE ENTRADA (Referencia obligatoria):
- Basate en el flujo lógico de: diagramas/03-escenarios-casos-de-uso/03-ver-agenda-exitoso.md
- Basate en los actores de: diagramas/02-casos-de-uso/02-caso-uso-ver-agenda-05.puml

REQUISITOS TÉCNICOS DE SALIDA:
1. Nomenclatura del archivo: El código debe guardarse como "04-actividad-ver-agenda-05.puml" en la carpeta "diagramas/04-diagramas-actividades/".
2. Estructura de Carriles (Swimlanes): Crea 3 carriles definidos: |Médico|, |Sistema| y |Base de Datos|.
3. Densidad de Actividades: El diagrama debe tener un mínimo de 10 actividades detalladas.
4. Trazabilidad: Los pasos deben ser un reflejo exacto del flujo principal del escenario de la Actividad 2.
5. Lógica de Control: Incluye un rombo de decisión (if/else) para representar situaciones como "No hay turnos para la fecha seleccionada".
6. Sintaxis: Utiliza la sintaxis moderna de PlantUML.

Genera el código PlantUML completo para integrar en la PR #89. Esta PR luego se mergeará manualmente a la PR #88 para su review.