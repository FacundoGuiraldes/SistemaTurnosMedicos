# Anexo - Fundamentos del Diseño Orientado a Objetos

**Mesa N° 645002 - Valeria Silva**

El diseño orientado a objetos, tal como lo desarrollan Larman y Pressman, propone modelar el software a partir de objetos con responsabilidades claras, colaboraciones explícitas y fronteras bien definidas. En un sistema de turnos médicos, ese enfoque permite representar entidades del dominio como pacientes, doctores, turnos, agenda y sala de espera sin mezclar decisiones de persistencia, comunicación o control de flujo en una sola clase.

Este anexo reúne los cuatro pilares del paradigma orientado a objetos y los vincula con la solución del proyecto **SistemaTurnosMedicos**. Cada fundamento se expone desde su definición conceptual, su relación con SOLID y patrones de diseño, y su aplicación concreta en las clases del sistema.

## Los cuatro fundamentos

- [Abstracción](./doo-abstraccion.md)
- [Encapsulamiento](./doo-encapsulamiento.md)
- [Herencia](./doo-herencia.md)
- [Polimorfismo](./doo-polimorfismo.md)

## Propósito del anexo

El objetivo de este material es demostrar que el modelado orientado a objetos no consiste solo en crear clases, sino en asignar responsabilidades estables, reducir acoplamiento y favorecer la extensibilidad. En términos de Larman, el diseño debe privilegiar la cohesión y la asignación responsable de tareas; en términos de Pressman, debe preservar mantenibilidad, trazabilidad y facilidad de evolución.

## Criterio de lectura

Cada subanexo mantiene la misma estructura: definición del pilar, relación con SOLID y patrones, ejemplo aplicado al proyecto, diagrama UML de referencia y un fragmento de código con justificación técnica. La intención es que el tribunal pueda seguir un criterio uniforme de análisis durante la defensa oral.

## Bibliografía base

- Larman, C. *Applying UML and Patterns: An Introduction to Object-Oriented Analysis and Design and the Unified Process*.
- Pressman, R. S. *Ingeniería del Software: un enfoque práctico*.
