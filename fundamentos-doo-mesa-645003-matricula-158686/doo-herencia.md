# Herencia

---

_La herencia es un principio fundamental de la programación orientada a objetos porque permite definir una clase base con atributos y comportamientos compartidos y, a partir de ella, crear subclases especializadas que reutilizan esa estructura sin duplicar lógica. En el sistema de turnos médicos del Dr. Molina, esta idea se refleja en la jerarquía de usuarios, donde una entidad común como Usuario concentra las operaciones básicas de autenticación y perfil, mientras que Paciente, Doctor y Secretaria agregan responsabilidades específicas del dominio. Desde el punto de vista de diseño, la herencia también está relacionada con el principio SOLID de sustitución de Liskov (LSP), porque las subclases deben poder reemplazar a la superclase sin alterar el comportamiento esperado del sistema. Además, este enfoque facilita el uso de patrones de diseño como Template Method, Strategy y Factory al establecer comportamientos reutilizables y puntos de extensión claros._

---

## Ejemplo en el proyecto

---

![Fragmento Diagrama UML - Herencia](../diagramas/01-diagrama-clases/capturas-pilares/poo-herencia-examen.png)

> **Ver detalles del diagrama:** [06-clases-diagrama-final.puml](../diagramas/01-diagrama-clases/06-clases-diagrama-final.puml)

### Descripción del Diagrama
La jerarquía elegida para este ejemplo es la formada por la clase base Usuario y las subclases concretas Paciente, Secretaria y Doctor. Usuario encapsula los datos y operaciones comunes a todos los actores del sistema: identificador, nombre, correo, teléfono y métodos como login(), logout() y modificarPerfil(). A partir de esta clase base, Paciente incorpora datos propios del paciente como dni, historial clínico y operaciones para solicitar o cancelar turnos; Doctor agrega información del profesional, como número de licencia, especialidad y consultorio; y Secretaria incorpora responsabilidades administrativas como registrar pacientes, programar turnos y gestionar agendas. De este modo, la herencia permite modelar una familia de objetos relacionados sin repetir la lógica básica en cada clase.

### Justificación Técnica
La herencia se aplica correctamente porque la clase base Usuario ofrece un contrato común que puede ser reutilizado por todas las subclases, mientras que cada una añade comportamiento específico sin perder la identidad de la superclase. Esta organización respeta el principio de sustitución de Liskov, ya que un objeto de tipo Doctor, Paciente o Secretaria puede utilizarse en contextos donde se espera un Usuario, sin que el sistema necesite conocer el tipo concreto para ejecutar operaciones compartidas como login() o recibirNotificacion(). La reutilización de código se concentra en Usuario, y la especialización ocurre en cada subclase, reduciendo duplicación y manteniendo una estructura más coherente y fácil de extender.

---

## Ejemplo de Código

---

```csharp
public abstract class Usuario
{
    protected string Id { get; set; }
    protected string Nombre { get; set; }
    protected string Email { get; set; }

    public virtual bool Login(string nombreUsuario, string contrasena)
    {
        return !string.IsNullOrWhiteSpace(nombreUsuario) &&
               !string.IsNullOrWhiteSpace(contrasena);
    }

    public void Logout()
    {
        // lógica común para cerrar sesión
    }
}

public class Paciente : Usuario
{
    public string Dni { get; private set; }

    public override bool Login(string nombreUsuario, string contrasena)
    {
        return base.Login(nombreUsuario, contrasena) &&
               Dni == nombreUsuario;
    }
}

public class Doctor : Usuario
{
    public string NumeroLicencia { get; private set; }
    public string Especialidad { get; private set; }

    public override bool Login(string nombreUsuario, string contrasena)
    {
        return base.Login(nombreUsuario, contrasena) &&
               NumeroLicencia == nombreUsuario;
    }
}
```

### Justificación Técnica del Código
El fragmento demuestra la herencia porque Paciente y Doctor heredan de Usuario y reutilizan sus atributos y métodos comunes, como Login() y Logout(). La clase base define el comportamiento general, mientras que cada subclase lo adapta a su contexto específico: Paciente valida su dni, y Doctor valida su número de licencia. Esto muestra que la herencia no solo reutiliza código, sino que también permite especializar el comportamiento sin romper el contrato de la superclase. Al mantener la misma interfaz de acceso, el sistema puede tratar a los objetos derivados como instancias de Usuario, lo que es esencial para aplicar correctamente el principio de sustitución de Liskov en el diseño orientado a objetos.
