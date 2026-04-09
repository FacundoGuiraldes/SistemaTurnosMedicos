# Documentación del Diseñador: Tarjetas CRC

## Prompt Utilizado
"Hola, por favor, necesito que leas los archivos anexos/introduccion.md y diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw como contexto. Y que identifiques las clases principales del sistema y propongas los campos de cada tarjeta CRC (nombre, superclase/subclase, pensamiento del objeto, responsabilidades, colaboraciones, propiedades) siguiendo la plantilla proporcionada."

## Archivos de Contexto
- `anexos/introduccion.md`: Narrativa con las reglas de negocio y flujos del sistema.
- `diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw`: Estructura visual preliminar de las clases.

## Ajustes Realizados
- **Normalización de Estructura:** Se transformaron los campos sugeridos inicialmente por la IA al formato de tabla de 4 columnas exigido, para garantizar la uniformidad.
- **Jerarquía de Usuarios:** Se refinó la clase **Usuario** como superclase para manejar la autenticación, derivando en **Paciente**, **Doctor** y **Secretaria** como subclases.
- **Redistribución de Responsabilidades:**
    - Se movió la lógica de disponibilidad y gestión de filas de espera a la clase **Agenda**.
    - Se definió a la clase **Sistema** como el orquestador principal (Singleton) para centralizar la base de datos y la auditoría.
- **Organización Documental:** Se separó cada tarjeta en un archivo `.md` individual dentro de la subcarpeta `tarjetas-crc/` y se creó el índice (`herramientas_agile.md`) para facilitar la navegación y lectura del diseño.