# Documentación del Diseño de Tarjetas CRC

## Prompt Utilizado

Hola, por favor, necesito que leas los archivos anexos/introduccion.md y diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw como contexto. Y que identifiques las clases principales del sistema y propongas los campos de cada tarjeta CRC (nombre, superclase/subclase, pensamiento del objeto, responsabilidades, colaboraciones, propiedades) siguiendo la plantilla proporcionada.

## Archivos de Contexto
- `anexos/introduccion.md`
- `diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw`

## Ajustes Realizados
- Se añadió la clase **Secretaria** con sus responsabilidades y colaboraciones.
- Se ajustó la colaboración de **Paciente** con **Secretaria**.
- Se revisó la responsabilidad de **Doctor** sobre "Registrar diagnósticos".
- Se agregó una propiedad "duracion" en **Turno**.
- Se añadió la responsabilidad de "Obtener disponibilidad" en **Agenda**.
- Se revisó la colaboración de **SalaEspera** con **Sistema**.
- Se consideró la creación de una clase **NotificacionService** en **Sistema**.