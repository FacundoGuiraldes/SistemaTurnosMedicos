# Abstracción

---

_La abstracción es un principio esencial de la programación orientada a objetos porque permite modelar solo aquello que es relevante para el problema, ocultando los detalles internos y exponiendo un contrato claro para interactuar con el objeto. En el sistema de turnos médicos del Dr. Molina, esta idea se observa en las interfaces de servicio y en las abstracciones de negocio que permiten que el sistema opere con conceptos del dominio sin depender de la implementación concreta. La abstracción se relaciona con el principio DIP porque el módulo de alto nivel depende de contratos y no de clases concretas, y con ISP porque los contratos se diseñan en torno a responsabilidades específicas. Además, esta forma de pensar se ve reflejada en patrones como Strategy, Factory Method y Repository, donde el comportamiento se encapsula detrás de una interfaz o de una abstracción compartida._

---

## Ejemplo en el proyecto

---

![Fragmento Diagrama UML - Abstracción](../diagramas/01-diagrama-clases/capturas-pilares/poo-abstraccion-examen.png)

> **Ver detalles del diagrama:** [06-clases-diagrama-final.puml](../diagramas/01-diagrama-clases/06-clases-diagrama-final.puml)

### Descripción del Diagrama
Se eligió la abstracción del servicio de persistencia del proyecto, representada por la interfaz `IPersistencia`, junto con su implementación concreta `PersistenciaService`. Esta abstracción se relaciona con la clase `Sistema`, que necesita guardar información de turnos sin conocer los detalles internos del almacenamiento. En el mismo diseño, el sistema también emplea interfaces como `INotificacionService` para abstraer la comunicación con el exterior, ocultando los detalles técnicos del canal de notificación.

### Justificación Técnica
La abstracción se cumple porque el cliente interactúa con un contrato esencial: “guardar turno”, sin conocer el detalle de cómo se implementa esa operación. La clase `Sistema` puede invocar `GuardarTurno()` sobre una referencia de tipo `IPersistencia`, aunque en tiempo de ejecución se esté usando la implementación concreta `PersistenciaService`. Esto permite ocultar reglas complejas, reducir el acoplamiento y facilitar la extensión del sistema. En términos de diseño, este enfoque mejora la mantenibilidad porque nuevos mecanismos de persistencia pueden agregarse sin modificar el comportamiento central del sistema, alineándose con DIP y con el espíritu de los patrones Repository y Strategy.

---

## Ejemplo de Código

---

```csharp
public interface IPersistencia
{
    void GuardarTurno(Turno turno);
}

public class PersistenciaService : IPersistencia
{
    public void GuardarTurno(Turno turno)
    {
        // lógica concreta de almacenamiento
    }
}

public class Sistema
{
    private readonly IPersistencia _persistencia;

    public Sistema(IPersistencia persistencia)
    {
        _persistencia = persistencia;
    }

    public void GuardarCambio(Turno turno)
    {
        _persistencia.GuardarTurno(turno);
    }
}
```

### Justificación Técnica del Código
En este fragmento, la interfaz `IPersistencia` representa la abstracción del servicio de almacenamiento que necesita `Sistema`. La clase cliente no necesita conocer si la información se guardará en memoria, en archivo o en una base de datos; solo requiere el contrato esencial de guardar un turno. `PersistenciaService` implementa esa abstracción con los detalles concretos de la persistencia, mientras que `Sistema` se mantiene enfocado en la lógica de negocio. Este diseño aplica la abstracción porque expone únicamente el comportamiento necesario para interactuar con el sistema, ocultando los detalles técnicos y favoreciendo la extensibilidad, el bajo acoplamiento y la coherencia con DIP.