# Principio de Sustitución de Liskov (LSP)

## Aplicación en el Sistema de Turnos Médicos (Jerarquía de Doctor)

El Principio de Sustitución de Liskov (LSP) establece que los objetos de un programa deben ser reemplazables por instancias de sus subtipos sin alterar la corrección de dicho programa. En otras palabras, las subclases deben ser sustituibles por sus superclases.

### Jerarquía de `Doctor` y sus Especialidades

Para ilustrar el `LSP`, consideramos una jerarquía simple para la clase `Doctor`:

*   **Superclase Abstracta:** `Doctor` (con el método `+ verAgenda()`)
*   **Subclase Concreta:** `Cardiologo` (que extiende `Doctor`)

El diagrama `01-solid-03-lsp.puml` muestra esta relación de herencia. La clase `Doctor` define un contrato básico, como la capacidad de `verAgenda()`. La clase `Cardiologo` hereda este comportamiento y, como subclase, puede ser utilizada en cualquier parte del sistema donde se espere un `Doctor`.

**Cumplimiento del LSP:**

Esta jerarquía cumple con el `LSP` porque:

*   **Sustituibilidad:** Un objeto de tipo `Cardiologo` puede ser utilizado en cualquier lugar del sistema donde se espere un objeto de tipo `Doctor` sin causar errores o comportamientos inesperados. Por ejemplo, si el sistema tiene una función que toma un `Doctor` y llama a `verAgenda()`, esta función operará correctamente si se le pasa una instancia de `Cardiologo`.
*   **Contrato de Comportamiento:** La subclase `Cardiologo` no altera la firma ni las precondiciones de los métodos de la clase `Doctor` (en este caso, `verAgenda()`). No modifica el comportamiento fundamental de los métodos heredados de una manera que rompa las expectativas de un cliente que interactúa con la superclase.
*   **Coherencia:** La relación "es-un" (`Cardiologo` es un `Doctor`) se mantiene semánticamente correcta, lo que es un indicador clave del cumplimiento del `LSP`.

### Impacto en el Diseño

La adhesión al `LSP` en esta jerarquía asegura que el sistema sea:

*   **Robusto:** Minimiza el riesgo de introducir bugs al extender el sistema con nuevas especialidades de doctores.
*   **Flexible:** Permite agregar nuevas especialidades médicas de manera sencilla, sin necesidad de modificar el código existente que trabaja con la abstracción `Doctor`.
*   **Mantenible:** Facilita la comprensión y el mantenimiento del código, ya que el comportamiento de los objetos es predecible a través de la jerarquía de herencia.