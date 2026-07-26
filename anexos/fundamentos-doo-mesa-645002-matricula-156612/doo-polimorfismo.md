# Polimorfismo

El polimorfismo es la capacidad de invocar el mismo mensaje sobre objetos distintos y obtener comportamientos diferentes según el tipo real del receptor. Larman lo asocia con la colaboración entre objetos que comparten un contrato, mientras que Pressman lo valora como una herramienta para mejorar extensibilidad y reducir condicionales dependientes del tipo. En un sistema orientado a objetos, el polimorfismo convierte la variación en una extensión natural del diseño.

Esta propiedad es especialmente útil cuando el sistema debe reaccionar de forma distinta ante un mismo evento sin que el componente que dispara el mensaje tenga que conocer todas las variantes posibles.

## Relación con SOLID

El polimorfismo es la base práctica del **OCP (Open/Closed Principle)**: si una operación se resuelve por despacho dinámico, agregar un nuevo comportamiento implica crear una nueva clase, no reescribir el código que ya la invoca. También está íntimamente ligado al **LSP**, porque solo hay polimorfismo útil cuando cada subtipo respeta el contrato del tipo base. De manera indirecta, favorece el **DIP**, ya que el código de alto nivel se apoya en interfaces y no en implementaciones concretas.

## Relación con patrones de diseño

El patrón **Observer** es uno de los ejemplos más claros de polimorfismo en acción: el sujeto notifica a observadores distintos a través de una interfaz común. **Factory Method** también se apoya en esta idea al delegar en subclases la creación de objetos concretos. En ambos casos, la lógica cliente trabaja contra una abstracción y el tipo real decide qué comportamiento se ejecuta.

## Ejemplo en el proyecto

En el proyecto, el caso más representativo es el patrón Observer aplicado a `TurnoMedico`. El sujeto mantiene una colección de `IObserverTurno` y, cuando ocurre una cancelación o una reprogramación, genera un `TurnoEvent` y notifica a todos los observadores. `NotificadorPaciente`, `NotificadorMedico` y `SistemaFacturacion` responden al mismo evento con acciones diferentes: envío de avisos, actualización de agenda o procesamiento contable.

Ese diseño evita condicionales del tipo "si el observador es paciente entonces...". El comportamiento correcto surge del tipo real del objeto y de la implementación concreta de `actualizar`.

## Diagrama UML


![Diagrama UML - Polimorfismo](./doo-polimorfismo.png)

[Ver diagrama en detalle](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/blob/feature/anexo-fundamentos-doo/Anexos/fundamentos-doo-mesa-645002-matricula-156612/doo-polimorfismo.puml)

*Diagrama fuente editable:* [doo-polimorfismo.puml](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/blob/feature/anexo-fundamentos-doo/Anexos/fundamentos-doo-mesa-645002-matricula-156612/doo-polimorfismo.puml)

## Ejemplo de código

```java
public interface IObserverTurno {
    void actualizar(TurnoEvent evento);
}

public class NotificadorPaciente implements IObserverTurno {
    @Override
    public void actualizar(TurnoEvent evento) {
        enviarMensaje(evento.getPacienteId(), "Su turno fue modificado: " + evento.getMotivo());
    }
}

public class NotificadorMedico implements IObserverTurno {
    @Override
    public void actualizar(TurnoEvent evento) {
        actualizarAgenda(evento.getMedicoId(), evento.getFechaNueva());
    }
}

public class SistemaFacturacion implements IObserverTurno {
    @Override
    public void actualizar(TurnoEvent evento) {
        registrarImpactoEconomico(evento.getId(), evento.getMotivo());
    }
}

public class EventDispatcher {
    private final List<IObserverTurno> observadores = new ArrayList<>();

    public void registrar(IObserverTurno observer) {
        observadores.add(observer);
    }

    public void despachar(TurnoEvent evento) {
        for (IObserverTurno observer : observadores) {
            observer.actualizar(evento);
        }
    }
}
```

## Justificación técnica

`EventDispatcher` solo conoce la interfaz `IObserverTurno`; por lo tanto, su lógica no cambia si mañana se agrega un nuevo observador. Esa es la ventaja técnica más importante del polimorfismo: el sujeto emite un mensaje y el receptor decide cómo responder. El código queda abierto a la extensión sin necesidad de tocar el flujo existente.

Desde el punto de vista del modelo, el polimorfismo evita que el sistema se transforme en una secuencia de `if/else` por tipo. Desde el punto de vista de la mantenibilidad, simplifica la incorporación de nuevas reacciones ante eventos del turno y mantiene el diseño alineado con Larman y Pressman.

## Bibliografía

- Larman, C. *Applying UML and Patterns: An Introduction to Object-Oriented Analysis and Design and the Unified Process*.
- Pressman, R. S. *Ingeniería del Software: un enfoque práctico*.
