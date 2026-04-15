# Documentación de Asistencia de IA - Modelador de Diagramas de Casos de Uso

**Archivos de contexto proporcionados:**
- `anexos/introduccion.md`

**Incidencia y Prompt utilizado:**
Debido a un error de límite de uso ("Error You have no quota") con GitHub Copilot Agent Mode, utilicé como contingencia mi asistente de IA alternativo. Le pasé la lista de los 5 casos de uso identificados con sus inclusiones y extensiones, y le pedí:
"Genera el código PlantUML aplicando estrictamente la sintaxis de la cátedra para asociaciones (líneas continuas), inclusiones (..> <<incluir>>) y extensiones (..> <<extender>>)."

**Ajustes manuales realizados al código de la IA:**
- Verifiqué que la dirección de las flechas de la relación `<<extender>>` apuntaran desde el caso de uso extendido hacia el caso base.
- Revisé que los diagramas renderizaran correctamente en VS Code antes de exportarlos a PNG.