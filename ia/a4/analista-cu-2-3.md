# Bitácora de Uso de Inteligencia Artificial - Analista Funcional CU2 y CU3

## Prompt Utilizado
```
Actúa como un Analista Funcional y Arquitecto de Software Senior experto en principios SOLID. Estoy resolviendo la consigna 3.1.2 de la Actividad Obligatoria Nro 4 para los Casos de Uso 2 y 3 de nuestro Sistema de Turnos Médicos.

Necesito diseñar los diagramas de clases específicos en PlantUML para:
- CU2: Cancelar Turno
- CU3: Registrar Llegada del Paciente

Para garantizar la coherencia absoluta con el trabajo previo del equipo, analiza detalladamente el contenido de los siguientes archivos de mi espacio de trabajo como fuentes de contexto obligatorias:
1. "diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw"
2. Los diagramas de "diagramas/02-casos-de-uso/" correspondientes a estos CU.
3. Los escenarios de "diagramas/03-escenarios-casos-de-uso/" correspondientes a estos CU.
4. Los diagramas de actividades de "diagramas/04-diagramas-actividades/" correspondientes a estos CU.
5. Los diagramas de secuencia de "diagramas/05-diagramas-secuencia/" correspondientes a estos CU.
6. Las tarjetas CRC involucradas en "herramientas-agile/tarjetas-crc/".

Requisitos mínimos para el diseño en PlantUML:
- Clases con nombres exactos alineados a las tarjetas CRC y diagramas de secuencia.
- Todos los atributos deben estar tipados.
- Todos los métodos deben incluir sus parámetros y tipo de retorno.
- Utilizar relaciones UML correctas (asociación, agregación, composición, dependencia y herencia).
- Cumplir de forma estricta con los principios SOLID (SRP, DIP) heredando la estructura base del CU1 de Valeria.

Por favor, generame únicamente el código PlantUML limpio para:
1. diagramas/01-diagrama-clases/02-clases-cancelar-turno-02.puml
2. diagramas/01-diagrama-clases/03-clases-registrar-llegada-03.puml
```

## Archivos de Contexto
- `diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw`: Estructura inicial del dominio y jerarquía de herencia de `Usuario`.
- Archivos de `diagramas/02-casos-de-uso/`: Modelado e imágenes con el alcance funcional de ambos flujos.
- Archivos de `diagramas/03-escenarios-casos-de-uso/`: Secuencia de pasos lógicos del flujo principal de cada caso de uso.
- `diagramas/04-diagramas-actividades/04-actividad-registrar-llegada-03.puml` y `04-actividad-cancelar-turno-02.puml`: Bifurcaciones y puntos de decisión del dominio.
- `diagramas/05-diagramas-secuencia/05-secuencia-registrar-llegada-registrar-llegada-del-paciente-03.puml` y `05-secuencia-cancelar-turno-02.puml`: Ciclo de vida de objetos y pasaje de mensajes del flujo operativo.
- Archivos de `herramientas-agile/tarjetas-crc/`: Definiciones operativas de responsabilidades para `Sistema`, `Secretaria`, `Paciente`, `Turno`, `Agenda` y `SalaEspera`.

## Ajustes Realizados
- **Análisis Técnico y Reformulación:** Se descartó una propuesta inicial de la IA que intentó generar un diagrama conceptual de casos de uso (con actores y burbujas de casos de uso), obligándola a reestructurar los archivos bajo una notación técnica de Diagrama de Clases Estructural POO.
- **Evolución y Desacoplamiento (SRP):** Se auditaron las responsabilidades del sistema propuestas por la IA, asegurando que las operaciones funcionales pesadas no recayeran sobre las entidades de datos puras (como `Turno` o `Paciente`), sino que fueran coordinadas por la clase controladora `Sistema` para evitar la violación del Principio de Responsabilidad Única.
- **Sincronización Semántica de Relaciones (DIP):** Se modificaron las relaciones lógicas en PlantUML que la IA propuso originalmente como dependencias transitorias (`..>`) hacia las interfaces de servicio, transformándolas en asociaciones estructurales continuas (`-->`), reflejando con exactitud la Inversión de Dependencias mediante atributos inyectados en la controladora `Sistema` (`ITurnoRepository`, `IAgendaService`, `INotificacionService`, `ITurnoService` e `ISalaEsperaService`).
- **Alineación de Firmas para Delegación Estructural:** Se corrigió la omisión por parte de la IA del método de acceso `+getPaciente(): Paciente` en la entidad `Turno`, incluyéndolo manualmente en ambos diagramas para permitir que el flujo lógico del pseudocódigo interactúe correctamente con los servicios inyectados.