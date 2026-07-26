# Encapsulamiento

El encapsulamiento consiste en ocultar el estado interno de un objeto y exponer solo operaciones controladas para interactuar con él. Larman lo entiende como una práctica esencial para preservar la integridad del modelo, y Pressman lo relaciona con la reducción de fragilidad frente a cambios internos. En un diseño orientado a objetos, encapsular no significa solo marcar atributos como privados: implica definir invariantes, proteger la consistencia y limitar los puntos de modificación del estado.

En un sistema de turnos médicos, esta idea es crítica porque hay entidades cuyo valor depende de múltiples reglas simultáneas. Si cualquier clase pudiera alterar directamente esos datos, el sistema perdería coherencia rápidamente.

## Relación con SOLID

El encapsulamiento sostiene el **SRP (Single Responsibility Principle)** porque cada clase administra su propio estado y su propia lógica de modificación. También habilita el **DIP**, ya que los detalles internos pueden cambiar sin afectar a los consumidores si estos dependen de abstracciones. Además, facilita el **OCP**, dado que una clase bien encapsulada puede extenderse por fuera sin exponer mecanismos internos que deban reescribirse.

## Relación con patrones de diseño

Patrones como **Facade** usan encapsulamiento a nivel arquitectónico: una clase de entrada simplifica y protege la interacción con varios subsistemas. **Observer** también se beneficia de este pilar, porque el sujeto encapsula su lista de observadores y controla cuándo y cómo emite los eventos. En ambos casos, el objetivo no es ocultar por ocultar, sino evitar que la complejidad interna se convierta en complejidad pública.

## Ejemplo en el proyecto

La clase `SalaEspera` es un caso representativo. Su estado interno puede incluir pacientes en espera, marcas horarias, prioridades y orden de atención. Ninguna de esas estructuras debería ser accesible de manera directa desde el exterior. Los clientes del sistema solo necesitan registrar llegadas, remover pacientes y consultar el listado de espera mediante métodos públicos cuidadosamente diseñados.

También `Turno` y `Agenda` se benefician del mismo principio: el cambio de estado de un turno o la administración de los turnos del día deben ocurrir por operaciones explícitas, no por manipulación libre de atributos.

## Diagrama UML


![Diagrama UML - Encapsulamiento](./doo-encapsulamiento.png)

[Ver diagrama en detalle](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/blob/feature/anexo-fundamentos-doo/Anexos/fundamentos-doo-mesa-645002-matricula-156612/doo-encapsulamiento.puml)

*Diagrama fuente editable:* [doo-encapsulamiento.puml](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/blob/feature/anexo-fundamentos-doo/Anexos/fundamentos-doo-mesa-645002-matricula-156612/doo-encapsulamiento.puml)

## Ejemplo de código

```java
public class SalaEspera implements ISalaEsperaService {
    private final List<Paciente> pacientesEnEspera = new ArrayList<>();
    private final Map<Paciente, LocalDateTime> horaLlegada = new HashMap<>();
    private final List<Paciente> ordenAtencion = new ArrayList<>();

    @Override
    public boolean registrarLlegada(Paciente paciente) {
        if (paciente == null) {
            return false;
        }

        LocalDateTime ahora = LocalDateTime.now();
        pacientesEnEspera.add(paciente);
        horaLlegada.put(paciente, ahora);
        ordenAtencion.add(paciente);
        return true;
    }

    public List<Paciente> obtenerPacientesEsperando() {
        return List.copyOf(ordenAtencion);
    }

    public boolean removerPaciente(Paciente paciente) {
        boolean removido = pacientesEnEspera.remove(paciente);
        horaLlegada.remove(paciente);
        ordenAtencion.remove(paciente);
        return removido;
    }
}
```

## Justificación técnica

La clase conserva sus estructuras internas como detalle privado y expone únicamente una API de negocio. De ese modo, si el criterio de atención cambia de una lista simple a una cola priorizada, el resto del sistema no necesita modificarse. Además, devolver una copia inmutable de la lista evita que un cliente altere el orden interno por accidente.

Desde la perspectiva de Pressman, este enfoque disminuye la fragilidad del sistema. Desde la perspectiva de Larman, mantiene una frontera clara entre responsabilidad y colaboración: `SalaEspera` administra su coherencia interna, mientras los clientes solo solicitan operaciones de negocio.

## Bibliografía

- Larman, C. *Applying UML and Patterns: An Introduction to Object-Oriented Analysis and Design and the Unified Process*.
- Pressman, R. S. *Ingeniería del Software: un enfoque práctico*.
