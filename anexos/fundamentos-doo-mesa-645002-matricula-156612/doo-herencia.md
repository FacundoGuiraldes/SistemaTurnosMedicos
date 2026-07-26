# Herencia

La herencia es el mecanismo por el cual una clase especializada reutiliza y amplía el comportamiento definido en una clase más general. En la visión de Larman, la generalización y la especialización permiten modelar el dominio con jerarquías coherentes; Pressman, por su parte, destaca que una estructura bien diseñada reduce duplicación y favorece la evolución controlada del sistema. La herencia es útil cuando existe una relación real de tipo "es un" y cuando la superclase representa un contrato estable para sus subclases.

En el proyecto, la herencia se usa para modelar roles del sistema que comparten identidad, datos de contacto y operaciones comunes, pero que al mismo tiempo poseen responsabilidades específicas. La clave es mantener la jerarquía pequeña y semánticamente correcta para no introducir rigidez innecesaria.

## Relación con SOLID

La herencia se relaciona principalmente con el **LSP (Liskov Substitution Principle)**: cualquier subclase debe poder reemplazar a su superclase sin romper el comportamiento esperado. También favorece el **OCP (Open/Closed Principle)**, ya que es posible extender una jerarquía agregando nuevas subclases sin modificar la clase base. Si la superclase expone una interfaz demasiado amplia, el diseño puede degradarse; por eso la herencia debe mantenerse alineada con el **ISP** y con responsabilidades cohesionadas.

## Relación con patrones de diseño

La herencia es central en patrones como **Template Method**, donde la clase base define el esqueleto del algoritmo y las subclases completan pasos concretos; también en **Factory Method**, donde la especialización permite decidir qué objeto concreto crear. Aunque no todo patrón depende de herencia, sí resulta frecuente que la jerarquía de clases aporte el punto de extensión para nuevas variantes del comportamiento.

## Ejemplo en el proyecto

El caso principal es la jerarquía `Usuario -> Paciente`, `Usuario -> Doctor` y `Usuario -> Secretaria`. La clase abstracta `Usuario` concentra lo común: nombre, email, teléfono, login, logout y modificación del perfil. Cada subclase agrega comportamiento específico del rol, pero conserva la identidad funcional de usuario del sistema.

Esta estructura es consistente con la lógica del dominio. Un paciente, un doctor y una secretaria pertenecen a la misma familia de actores, pero cumplen funciones diferentes. La superclase evita duplicar campos y operaciones comunes, y las subclases permiten especializar responsabilidades sin mezclar reglas de negocio de un rol con las de otro.

## Diagrama UML


![Diagrama UML - Herencia](./doo-herencia.png)

[Ver diagrama en detalle](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/blob/feature/anexo-fundamentos-doo/Anexos/fundamentos-doo-mesa-645002-matricula-156612/doo-herencia.puml)

*Diagrama fuente editable:* [doo-herencia.puml](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/blob/feature/anexo-fundamentos-doo/Anexos/fundamentos-doo-mesa-645002-matricula-156612/doo-herencia.puml)

## Ejemplo de código

```java
public abstract class Usuario {
    private String nombre;
    private String email;
    private String telefono;

    public String getNombre() {
        return nombre;
    }

    public String getEmail() {
        return email;
    }

    public String getTelefono() {
        return telefono;
    }

    public void modificarPerfil(String nombre, String email, String telefono) {
        this.nombre = nombre;
        this.email = email;
        this.telefono = telefono;
    }

    public String getNombreCompleto() {
        return nombre;
    }
}

public class Paciente extends Usuario {
    private String numeroHistorial;
    private String dni;

    public Turno solicitarTurno(LocalDate fecha, LocalTime hora, String especialidad) {
        return new Turno(fecha, hora, especialidad, this);
    }

    public boolean cancelarTurno(Turno turno, String motivo) {
        return turno.cancelar(this, motivo);
    }
}

public class Doctor extends Usuario {
    private String matricula;
    private String especialidad;

    public List<Turno> verAgenda(LocalDate fecha) {
        return agenda.obtenerTurnosDelDia(fecha);
    }
}

public class Secretaria extends Usuario {
    private String departamento;

    public Paciente registrarPaciente(Map<String, String> datos) {
        return new Paciente(datos);
    }
}
```

## Justificación técnica

`Usuario` funciona como una abstracción general de los actores humanos del sistema, mientras que `Paciente`, `Doctor` y `Secretaria` especializan ese modelo de acuerdo con sus tareas reales. La herencia evita repetir atributos y servicios comunes, pero además deja explícita la relación conceptual entre los roles. Eso es importante desde el punto de vista del análisis: el diagrama comunica la estructura del dominio de manera más clara que si cada rol fuera una clase aislada.

El diseño también preserva el LSP. Ninguna subclase debería debilitar las reglas definidas por `Usuario`; por ejemplo, si `Usuario` garantiza que existe un nombre y un email válidos, las subclases deben sostener esa promesa. Cuando la jerarquía se mantiene pequeña y semánticamente correcta, la herencia agrega valor real al diseño y no solo reutilización mecánica.

## Bibliografía

- Larman, C. *Applying UML and Patterns: An Introduction to Object-Oriented Analysis and Design and the Unified Process*.
- Pressman, R. S. *Ingeniería del Software: un enfoque práctico*.
