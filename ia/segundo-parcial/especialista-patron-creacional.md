# Bitácora de Uso de Inteligencia Artificial - Especialista Creacional

## 1. Archivos de Contexto Referenciados
Para que la IA comprendiera la arquitectura existente y los lineamientos de diseño previos, se seleccionaron explícitamente los siguientes archivos como fuentes de contexto obligatorias en la interfaz del chat:
* `diagramas/01-diagrama-clases/06-clases-diagrama-final.puml`
* `diagramas/01-diagrama-clases/01-solid-01-srp.puml`
* `diagramas/01-diagrama-clases/01-solid-02-ocp.puml`
* `diagramas/01-diagrama-clases/01-solid-03-lsp.puml`
* `diagramas/01-diagrama-clases/01-solid-04-isp.puml`
* `diagramas/01-diagrama-clases/01-solid-05-dip.puml`

---

## 2. Prompt Utilizado
Se emitió la siguiente consulta estructurada en el chat para obtener la propuesta técnica:

```text
Actúa como un Arquitecto de Software Experto. Analiza los archivos provistos en el contexto, especialmente "06-clases-diagrama-final.puml". 

NO crees ni modifiques ningún archivo de mi espacio de trabajo. Solo respóndeme en texto dentro de esta ventana de chat con lo siguiente:

1. ¿Qué problema de acoplamiento por instanciación directa ("new") encontrás en el diagrama de clases final en el sistema de turnos médicos?
2. Proponeme la estructura teórica del patrón Factory Method para solucionarlo.
3. Mostrame el bloque de código PlantUML que proponés para solucionar este problema (escríbelo acá en el chat dentro de un bloque de código markdown, no generes el archivo).
```
---

## 3. Output de la IA
El asistente identificó con éxito que las clases `Sistema` y `Secretaria` instanciaban directamente `Turno`, y que `ServicioNotificaciones` instanciaba directamente `Notificacion` de forma monolítica. 

Propuso solucionar ambos acoplamientos implementando el patrón **Factory Method** por partida doble, abstrayendo la creación mediante las interfaces creadoras `ITurnoFactory` e `INotificacionFactory`, y devolviendo subclases concretas de productos (`TurnoPresencial`, `TurnoVirtual`, `EmailNotificacion`, `WhatsAppNotificacion`, etc.), proveyendo además el correspondiente bloque de código PlantUML consolidado.

---

## 4. Ajustes Realizados e Iteraciones Relevantes al Output
Aunque el diseño provisto por la IA era de alta calidad, se realizaron los siguientes ajustes manuales específicos para asegurar la correcta integración en el repositorio del examen:

* **Ajuste y Sincronización de Nomenclatura Externa:** El output de la IA sugería nombres genéricos o predeterminados para guardar los archivos. Se ignoró esa recomendación de nombres y se ajustó manualmente el guardado físico a la nomenclatura exacta exigida en la sección de entregables del rol (`01-patron-creacional-factory.puml` y `01-patron-creacional-factory.png`).
* **Refactorización de Dependencias por Inyección:** Se analizó rigurosamente el código de las clases del sistema refactorizadas por la IA (`Sistema`, `Secretaria` y `ServicioNotificaciones`). Se validó e iteró visualmente que la relación con las fábricas se diera estrictamente por **Inyección de Dependencias en el Constructor**, garantizando que el acoplamiento fuera hacia las abstracciones de las fábricas y no hacia implementaciones concretas, cumpliendo así con el principio **DIP** analizado durante las clases.
* **Consolidación Estructural de Métodos:** Se controló que los métodos del bloque sugerido por la IA mantuvieran consistencia textual absoluta con los métodos originales registrados en `06-clases-diagrama-final.puml` (`solicitarTurno`, `registrarTurno`, etc.) evitando que la IA inventara firmas nuevas que rompieran la trazabilidad con el trabajo de los compañeros de equipo.