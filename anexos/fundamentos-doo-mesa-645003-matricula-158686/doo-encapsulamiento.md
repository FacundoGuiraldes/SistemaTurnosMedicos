# Encapsulamiento

## Explicación

El encapsulamiento es el pilar del Diseño Orientado a Objetos (DOO) que consiste en empaquetar datos (atributos) y métodos dentro de una misma entidad o clase, ocultando el estado interno del objeto frente al exterior y exponiendo únicamente una interfaz controlada mediante modificadores de visibilidad (privado, protegido, público).

Este principio garantiza la integridad de los datos y se relaciona con los principios SOLID:
- **SRP (Responsabilidad Única):** Cada clase asume la responsabilidad exclusiva de proteger y gestionar la validez de su propio estado.
- **OCP (Abierto/Cerrado):** Permite modificar o evolucionar la implementación y las reglas internas de una clase sin afectar a los clientes externos que consumen su interfaz pública.

En términos de arquitectura de software, el encapsulamiento facilita la aplicación de patrones de comportamiento como **State**, donde las transiciones de estado se controlan de forma segura evitando modificaciones inválidas o inconsistentes.

## Ejemplo en el proyecto

![Fragmento Diagrama UML - Encapsulamiento](../diagramas/01-diagrama-clases/capturas-pilares/poo-encapsulamiento-examen.png)

> **Ver detalles del diagrama:** [06-clases-diagrama-final.puml](../diagramas/01-diagrama-clases/06-clases-diagrama-final.puml)

Se presenta la estructura interna de clases del dominio como `Turno`, `Paciente` y `Agenda`, enfocándose en el uso de visibilidad privada para proteger sus atributos esenciales.

### Descripción y Justificación Técnica

El diagrama refleja el principio de encapsulamiento mediante el uso de simbología UML de visibilidad privada (`-`) en atributos sensibles (como `_estado`, `_dni`, `_fecha`, `_turnos`) y pública (`+`) para métodos y propiedades expuestos.

Las clases seleccionadas cumplen con este fundamento debido a que el estado interno de los objetos no puede ser alterado arbitrariamente desde fuera. En la clase `Turno`, el cambio de estado (ej. pasando a `Atendido` o `Cancelado`) está restringido a métodos específicos (`Confirmar()`, `Cancelar()`, `MarcarAtendido()`), garantizando que cualquier transición respete las reglas de negocio antes de actualizar las variables de estado.

## Ejemplo de Código

```csharp
public class Turno
{
    private readonly string _id;
    private DateTime _fecha;
    private TimeSpan _hora;
    private EstadoTurno _estado;
    private string _motivoConsulta;

    public Turno(string id, DateTime fecha, TimeSpan hora)
    {
        _id = id;
        _fecha = fecha;
        _hora = hora;
        _estado = EstadoTurno.Disponible;
        _motivoConsulta = string.Empty;
    }

    public string Id => _id;
    public DateTime Fecha => _fecha;
    public TimeSpan Hora => _hora;
    public EstadoTurno Estado => _estado;

    public void Confirmar()
    {
        if (_estado != EstadoTurno.Reservado)
            throw new InvalidOperationException("El turno no puede confirmarse en este estado.");

        _estado = EstadoTurno.Pendiente;
    }

    public void Cancelar(string motivo)
    {
        if (_estado == EstadoTurno.Atendido || _estado == EstadoTurno.Cancelado)
            throw new InvalidOperationException("No se puede cancelar un turno ya atendido o cancelado.");

        _motivoConsulta = motivo;
        _estado = EstadoTurno.Cancelado;
    }

    public void MarcarAtendido()
    {
        if (_estado != EstadoTurno.Pendiente)
            throw new InvalidOperationException("Solo se puede atender un turno pendiente.");

        _estado = EstadoTurno.Atendido;
    }
}

Este fragmento demuestra el encapsulamiento al mantener los campos de estado en ámbito privado (private), restringiendo su modificación externa. Los datos se exponen únicamente mediante propiedades de lectura (get) y los cambios de estado se delegan a métodos con lógica de validación explícita (Confirmar(), Cancelar(), MarcarAtendido()), preservando la invariante del objeto y evitando inconsistencias en el dominio.