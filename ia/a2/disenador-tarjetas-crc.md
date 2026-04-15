# Documentación del Diseñador: Tarjetas CRC

## Prompt Utilizado
"Hola, por favor, necesito que leas los archivos anexos/introduccion.md y diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw como contexto. Y que identifiques las clases principales del sistema y propongas los campos de cada tarjeta CRC (nombre, superclase/subclase, pensamiento del objeto, responsabilidades, colaboraciones, propiedades) siguiendo la plantilla proporcionada."

## Archivos de Contexto
- `anexos/introduccion.md`: Narrativa con las reglas de negocio y flujos del sistema.
- `diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw`: Estructura visual preliminar de las clases.

## Ajustes Realizados
- **Normalización de Formato:** Se transformó el formato de lista simple de Copilot al formato de tabla de 4 columnas (Responsabilidades, Colaboradores, Pensamiento del Objeto, Propiedades) exigido por el estándar del proyecto.
- **Evolución del Rol del Sistema:** Se eliminó la concepción del Sistema como un gestor directo de base de datos y mensajes. Ahora actúa como un **Orquestador de Servicios**, mejorando la mantenibilidad y el desacoplamiento.
- **Refinamiento de la Clase Paciente:** Se corrigió la lógica donde el paciente "ejecutaba" acciones. Ahora el Paciente **provee datos y notifica intenciones**, respetando mejor la inversión de control.
- **Optimización del Flujo de Asistencia:** Se eliminó la redundancia de la responsabilidad `registrarLlegada` que aparecía en casi todas las clases iniciales. Se centralizó en la **Secretaria** como ejecutora operativa.
- **Enriquecimiento de Atributos:** - Se agregó `especialidad` a la clase **Turno** para permitir búsquedas y filtros precisos.
    - Se incorporó el manejo de **Estados Dinámicos** (Esperando, En consulta, Finalizado) en la **Sala de Espera**, permitiendo una trazabilidad real del flujo de atención que el informe inicial no contemplaba detalladamente.
- **Claridad en la Lógica de Agenda:** Se separó la "configuración de reglas" (responsabilidad de Agenda) de la "validación de colisiones" (responsabilidad de Sistema), logrando un diseño más robusto ante cambios en las reglas de negocio.

## Iteración Final: Refactorización por Feedback Técnico
Tras una revisión por pares (Peer Review) del equipo, se realizó una última fase de ajustes manuales y asistidos para garantizar la máxima coherencia técnica:

- **Sincronización de Atributos:** Se restauraron atributos clave del boceto original que se habían omitido (ej. `departamento` en Secretaria y colecciones de `usuarios`, `turnos` y `agendas` en Sistema).
- **Activación de Responsabilidades:** Se revirtió la lógica pasiva en los actores principales. El Paciente y el Doctor ahora poseen **responsabilidades activas** (ej. "Solicitar turno" en lugar de "Proveer datos"), alineando el diseño con el comportamiento real de los objetos en un sistema orientado a eventos.
- **Definición de Abstracción:** Se marcó explícitamente a la clase `Usuario` como **Abstracta**, impidiendo instancias genéricas y fortaleciendo la jerarquía de herencia.
- **Cumplimiento de RF Específicos:** Se integró formalmente la responsabilidad de notificaciones para cubrir el **RF3** y se refinó la interacción de la **Sala de Espera** para la gestión de colas de asistencia.