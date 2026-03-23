## Descripción del paradigma orientado a objetos
El paradigma orientado a objetos es una forma de programar que organiza el software en entidades llamadas "objetos", los cuales modelan cosas del mundo real combinando sus datos (atributos) y su comportamiento (métodos). Es fundamental porque permite crear sistemas más modulares, seguros, fáciles de mantener y en los que el código se puede reutilizar.

## Los cuatro fundamentos de POO
* **Abstracción:** Es simplificar la complejidad del mundo real modelando solo los aspectos esenciales relevantes para el sistema. 
  * *Ejemplo:* En el sistema del consultorio, del objeto "Paciente" solo abstraemos datos vitales como su nombre, DNI y obra social, ignorando detalles irrelevantes como su color de pelo.
* **Encapsulamiento:** Ocultar la implementación interna de un objeto y exponer sólo las interfaces públicas para promover la seguridad. 
  * *Ejemplo:* El objeto "Turno" oculta cómo guarda internamente la fecha y hora, y solo permite que la secretaria lo modifique a través de un método válido y seguro como `cambiar_fecha()`.
* **Herencia:** Es un mecanismo que permite que un objeto herede propiedades y comportamientos de otro objeto, fomentando la reutilización del código. 
  * *Ejemplo:* Podemos tener una clase general llamada "Persona" (con atributos como nombre y DNI) de la cual heredan sus características clases más específicas como "Paciente" y "Medico".
* **Polimorfismo:** Se refiere a la capacidad de los objetos de diferentes clases para responder de manera diferente a un mismo mensaje u orden. 
  * *Ejemplo:* La orden o método `calcular_honorarios()` funcionará y calculará resultados diferentes si se le pide a un Médico Clínico que si se le pide a un Médico Psiquiatra.
