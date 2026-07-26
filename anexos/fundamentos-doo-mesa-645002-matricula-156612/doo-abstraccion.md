# Abstracción

La abstracción consiste en identificar lo esencial de un problema y omitir los detalles que no son relevantes para la responsabilidad que debe cumplir un objeto. Larman la vincula con la modelación del dominio a partir de conceptos comprensibles para el negocio, mientras que Pressman la relaciona con la reducción de complejidad y de dependencias innecesarias entre módulos. En diseño orientado a objetos, abstraer no significa "simplificar demasiado", sino definir el contrato correcto para que cada componente exponga solo lo que otros necesitan saber.

En un sistema clínico, la abstracción permite que la lógica de negocio trabaje sobre conceptos como repositorios, servicios o eventos sin depender del mecanismo físico de almacenamiento, del formato de intercambio o de la tecnología concreta utilizada. Ese aislamiento facilita pruebas, mantenimiento y evolución tecnológica.

## Relación con SOLID

La abstracción es el soporte natural del **DIP (Dependency Inversion Principle)**: los módulos de alto nivel no dependen de detalles de bajo nivel, sino de contratos. También favorece el **OCP (Open/Closed Principle)**, porque al depender de una interfaz el sistema puede incorporar nuevas implementaciones sin modificar a los consumidores. De manera indirecta, ayuda al **ISP (Interface Segregation Principle)** al promover contratos pequeños y específicos, y al **LSP (Liskov Substitution Principle)** al exigir que toda implementación respete el comportamiento prometido por la abstracción.

## Relación con patrones de diseño

La abstracción aparece de forma explícita en patrones como **Factory Method**, donde la creación se delega a contratos y no a clases concretas; en **Facade**, donde una interfaz de alto nivel oculta la coordinación de subsistemas; y en **Observer**, donde el sujeto notifica a una familia de observadores mediante una interfaz común. En todos los casos, la clave no es ocultar información por sí misma, sino estabilizar las colaboraciones del sistema.

## Ejemplo en el proyecto

El ejemplo más claro en el proyecto es la relación entre `Sistema`, `ITurnoRepository` e `IPacienteRepository`. La clase `Sistema` concentra la coordinación de los casos de uso, pero no conoce cómo se persisten los datos. En cambio, trabaja sobre interfaces: consulta turnos, verifica duplicidad de pacientes y actualiza información mediante contratos. La implementación concreta `PersistenciaService` satisface esos contratos sin obligar a `Sistema` a depender de una base de datos, de archivos o de una API externa.

Esa decisión es coherente con el análisis de Larman: el objeto de alto nivel conserva una responsabilidad de coordinación y delega los detalles a colaboraciones bien definidas. También responde al criterio de Pressman de minimizar acoplamientos para que un cambio de infraestructura no impacte en el núcleo funcional del sistema.

## Diagrama UML


![Diagrama UML - Abstracción](./doo-abstraccion.png)

[Ver diagrama en detalle](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/blob/feature/anexo-fundamentos-doo/Anexos/fundamentos-doo-mesa-645002-matricula-156612/doo-abstraccion.puml)

*Diagrama fuente editable:* [doo-abstraccion.puml](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/blob/feature/anexo-fundamentos-doo/Anexos/fundamentos-doo-mesa-645002-matricula-156612/doo-abstraccion.puml)

## Ejemplo de código

```java
public interface ITurnoRepository {
    Turno buscarPorId(String turnoId);
    boolean actualizar(Turno turno);
    List<Turno> obtenerTurnosPorFecha(LocalDate fecha, Doctor doctor);
}

public interface IPacienteRepository {
    boolean existePorDni(String dni);
    void guardar(Paciente paciente);
}

public class Sistema {
    private final ITurnoRepository turnoRepository;
    private final IPacienteRepository pacienteRepository;

    public Sistema(ITurnoRepository turnoRepository, IPacienteRepository pacienteRepository) {
        this.turnoRepository = turnoRepository;
        this.pacienteRepository = pacienteRepository;
    }

    public boolean cancelarTurno(String turnoId, String motivo) {
        Turno turno = turnoRepository.buscarPorId(turnoId);
        turno.cancelar(null, motivo);
        return turnoRepository.actualizar(turno);
    }

    public boolean validarPacienteDuplicado(String dni) {
        return pacienteRepository.existePorDni(dni);
    }
}

public class PersistenciaService implements ITurnoRepository, IPacienteRepository {
    @Override
    public Turno buscarPorId(String turnoId) {
        return baseDeDatos.findTurnoById(turnoId);
    }

    @Override
    public boolean actualizar(Turno turno) {
        return baseDeDatos.updateTurno(turno);
    }

    @Override
    public List<Turno> obtenerTurnosPorFecha(LocalDate fecha, Doctor doctor) {
        return baseDeDatos.findTurnosByFechaAndDoctor(fecha, doctor);
    }

    @Override
    public boolean existePorDni(String dni) {
        return baseDeDatos.existsPacienteByDni(dni);
    }

    @Override
    public void guardar(Paciente paciente) {
        baseDeDatos.insertPaciente(paciente);
    }
}
```

## Justificación técnica

`Sistema` depende de dos abstracciones y no de una clase concreta de persistencia. Eso permite reemplazar `PersistenciaService` por una implementación en memoria para pruebas, por un repositorio SQL en producción o por un adaptador remoto sin modificar el flujo de los casos de uso. La abstracción también mejora la legibilidad del diseño: cualquier lector del modelo puede comprender qué necesita el sistema antes de revisar cómo se resuelve técnicamente.

En términos de diseño orientado a objetos, la abstracción es el punto de partida para desacoplar decisiones y para organizar el sistema en torno a contratos estables. Por eso aparece de forma reiterada en este proyecto y en patrones como Facade, Factory Method y Observer.

## Bibliografía

- Larman, C. *Applying UML and Patterns: An Introduction to Object-Oriented Analysis and Design and the Unified Process*.
- Pressman, R. S. *Ingeniería del Software: un enfoque práctico*.
