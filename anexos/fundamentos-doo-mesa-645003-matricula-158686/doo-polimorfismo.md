# Polimorfismo

## Explicación

El polimorfismo es el principio de la Programación Orientada a Objetos (POO) que permite a objetos de distintas clases responder de manera diferente y única a un mismo mensaje o llamada a un método común. Esto se logra mediante ligadura tardía (*Late Binding*), donde el comportamiento concreto a ejecutar se determina en tiempo de ejecución según la instancia real del objeto.

Este principio se vincula estrechamente con los principios SOLID:
- **OCP (Abierto/Cerrado):** Permite extender el comportamiento del sistema agregando nuevas clases derivadas sin necesidad de modificar el código cliente existente.
- **LSP (Sustitución de Liskov):** Asegura que las distintas implementaciones polimórficas mantengan el contrato y la coherencia del tipo base.

En arquitectura de software, el polimorfismo es el motor fundamental para patrones como **Strategy**, **State** y **Factory Method**, donde una operación invocado sobre una abstracción desencadena algoritmos o comportamientos adaptados al contexto u objeto actual.

## Ejemplo en el proyecto

![Fragmento Diagrama UML - Polimorfismo](../diagramas/01-diagrama-clases/capturas-pilares/poo-polimorfismo-examen.png)

> **Ver detalles del diagrama:** [06-clases-diagrama-final.puml](../diagramas/01-diagrama-clases/06-clases-diagrama-final.puml)

Se presenta la invocación del método abstracto/virtual `Login()` desde la clase de alto nivel `Sistema` hacia la abstracción base `Usuario`, la cual es resuelta polimórficamente por las subclases `Paciente`, `Doctor` y `Secretaria`.

### Descripción y Justificación Técnica

El diagrama refleja el principio de polimorfismo al mostrar que la clase `Sistema` invoca el mensaje `Login()` sobre una referencia de tipo abstracto `Usuario`, sin conocer qué clase concreta ejecutará la acción en tiempo de ejecución.

Las clases seleccionadas cumplen con este fundamento debido a que cada subclase (`Paciente`, `Doctor`, `Secretaria`) sobrescribe la operación `Login()` para implementar sus propias reglas de autenticación (ej. validación por DNI en pacientes vs. por número de licencia en doctores). De este modo, la clase `Sistema` permanece desacoplada de los tipos específicos, permitiendo incorporar nuevos tipos de usuarios sin modificar el algoritmo de autenticación.

## Ejemplo de Código

```csharp
public abstract class Usuario
{
    public abstract bool Login(string nombreUsuario, string contrasena);
}

public class Paciente : Usuario
{
    public override bool Login(string nombreUsuario, string contrasena)
    {
        return nombreUsuario == "12345678" && contrasena == "clavePaciente";
    }
}

public class Doctor : Usuario
{
    public override bool Login(string nombreUsuario, string contrasena)
    {
        return nombreUsuario == "LIC-001" && contrasena == "claveDoctor";
    }
}

public class Sistema
{
    public bool IniciarSesion(Usuario usuario, string nombreUsuario, string contrasena)
    {
        return usuario.Login(nombreUsuario, contrasena);
    }
}

Este fragmento demuestra el polimorfismo al invocar usuario.Login(...) dentro de Sistema.IniciarSesion(...). La llamada al método depende exclusivamente del contrato abstracto Usuario. En tiempo de ejecución, C# resuelve dinámicamente si debe ejecutar la implementación de Paciente o Doctor, respondiendo de forma especializada según el objeto recibido sin requerir condicionales (if/switch) por tipo de clase.