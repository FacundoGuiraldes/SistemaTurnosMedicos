# Polimorfismo

## Explicación

El polimorfismo es uno de los fundamentos del Diseño Orientado a Objetos y permite que distintos objetos respondan de manera diferente ante un mismo mensaje.

En términos técnicos, una clase puede trabajar con una referencia general, como una interfaz o una clase base, y en tiempo de ejecución se ejecuta el comportamiento correspondiente al tipo concreto del objeto.

Esto permite escribir código más flexible, desacoplado y extensible, porque el sistema no necesita preguntar de qué clase concreta es cada objeto para decidir qué operación ejecutar.

El polimorfismo suele aparecer junto con la herencia y las interfaces. En ambos casos existe un contrato común, pero cada implementación concreta puede resolver ese contrato de una forma distinta.

## Relación con los principios SOLID y los patrones de diseño

El polimorfismo se relaciona directamente con el principio **Liskov Substitution Principle (LSP)**, porque una clase concreta debe poder reemplazar a su abstracción sin romper el comportamiento esperado por el sistema.

También se relaciona con **Open/Closed Principle (OCP)**. Si el sistema trabaja contra una interfaz, se pueden agregar nuevas implementaciones sin modificar el código que ya usa esa interfaz.

Además, se vincula con **Dependency Inversion Principle (DIP)**, ya que los módulos principales dependen de abstracciones y no de clases concretas.

En el proyecto, el ejemplo más claro aparece en el patrón **Observer**: `TurnoMedico` notifica eventos a una colección de objetos `IObserverTurno`, sin conocer si cada observador es un `NotificadorPaciente`, un `NotificadorMedico` o un `SistemaFacturacion`.

Este diseño permite que todos los observadores reciban el mismo mensaje, `actualizar(evento)`, pero cada uno lo procese según su propia responsabilidad.

---

## Ejemplo en el proyecto

Para representar el polimorfismo se seleccionaron los siguientes elementos del proyecto:

- `IObserverTurno`;
- `TurnoMedico`;
- `TurnoEvent`;
- `NotificadorPaciente`;
- `NotificadorMedico`;
- `SistemaFacturacion`.

La interfaz `IObserverTurno` define el contrato común:

```text
actualizar(evento: TurnoEvent): void
```

Las clases `NotificadorPaciente`, `NotificadorMedico` y `SistemaFacturacion` implementan ese mismo método, pero cada una lo resuelve con una lógica distinta.

### Diagrama UML

![Diagrama UML de polimorfismo](doo-polimorfismo.png)

[Ver el diagrama UML de polimorfismo en detalle](doo-polimorfismo.puml)

### Descripción del diagrama

El diagrama muestra a `IObserverTurno` como una interfaz que declara la operación `actualizar(evento: TurnoEvent)`.

Las clases `NotificadorPaciente`, `NotificadorMedico` y `SistemaFacturacion` implementan esa interfaz. Esto significa que todas pueden ser utilizadas mediante el tipo general `IObserverTurno`.

La clase `TurnoMedico` mantiene una colección de observadores:

```text
observadores: List<IObserverTurno>
```

Cuando se produce un cambio sobre un turno, `TurnoMedico` crea un `TurnoEvent` y notifica a cada observador llamando al mismo método `actualizar(evento)`.

El punto importante es que `TurnoMedico` no necesita conocer el tipo concreto de cada observador. El método ejecutado se resuelve en tiempo de ejecución según el objeto real:

- `NotificadorPaciente` puede enviar una notificación al paciente;
- `NotificadorMedico` puede actualizar o sincronizar la agenda médica;
- `SistemaFacturacion` puede registrar el impacto administrativo o contable del cambio.

### Justificación técnica

Las clases seleccionadas cumplen con el fundamento de polimorfismo porque comparten un mismo contrato y ofrecen distintas implementaciones concretas.

`IObserverTurno` define el mensaje común, mientras que cada observador decide cómo responder a ese mensaje.

De esta forma, `TurnoMedico` puede recorrer una lista de `IObserverTurno` y ejecutar:

```java
observer.actualizar(evento);
```

sin utilizar condicionales como:

```java
if (observer instanceof NotificadorPaciente)
```

ni estructuras `switch` basadas en tipos concretos.

Esto reduce el acoplamiento y respeta OCP: si en el futuro se agrega un nuevo observador, por ejemplo `RegistroAuditoria`, sólo debe implementar `IObserverTurno` y suscribirse al turno. No hace falta modificar la lógica de notificación de `TurnoMedico`.

---

## Ejemplo de código

El siguiente pseudocódigo representa la aplicación del polimorfismo mediante el patrón Observer usado en el proyecto.

```java
public interface IObserverTurno {

    void actualizar(TurnoEvent evento);
}

public class NotificadorPaciente
    implements IObserverTurno {

    @Override
    public void actualizar(TurnoEvent evento) {
        enviarMensajeAlPaciente(
            "Su turno fue modificado: "
                + evento.getMotivo()
        );
    }
}

public class NotificadorMedico
    implements IObserverTurno {

    @Override
    public void actualizar(TurnoEvent evento) {
        sincronizarAgendaMedica(
            evento
        );
    }
}

public class SistemaFacturacion
    implements IObserverTurno {

    @Override
    public void actualizar(TurnoEvent evento) {
        registrarImpactoAdministrativo(
            evento
        );
    }
}

public class TurnoMedico {

    private List<IObserverTurno> observadores =
        new ArrayList<>();

    public void suscribir(
        IObserverTurno observer
    ) {
        observadores.add(observer);
    }

    public void cancelar(String motivo) {
        TurnoEvent evento =
            new TurnoEvent(this, motivo);

        notificar(evento);
    }

    private void notificar(
        TurnoEvent evento
    ) {
        for (IObserverTurno observer : observadores) {
            observer.actualizar(evento);
        }
    }
}
```

### Justificación técnica del código

El fragmento demuestra polimorfismo porque `TurnoMedico` trabaja con una lista de objetos declarados como `IObserverTurno`, no con una lista de clases concretas.

Aunque todos los elementos de la lista reciben el mismo mensaje:

```java
observer.actualizar(evento);
```

cada clase responde de una forma distinta:

- `NotificadorPaciente` comunica el cambio al paciente;
- `NotificadorMedico` sincroniza la agenda médica;
- `SistemaFacturacion` registra el impacto administrativo.

El comportamiento no se decide mediante condicionales escritos en `TurnoMedico`, sino mediante despacho dinámico: Java selecciona en tiempo de ejecución la implementación de `actualizar()` correspondiente al objeto real.

Por eso el diseño es extensible. Para agregar un nuevo comportamiento ante cambios de turno, alcanza con crear otra clase que implemente `IObserverTurno`. La lógica principal de `TurnoMedico` permanece cerrada a modificaciones y abierta a nuevas extensiones.
