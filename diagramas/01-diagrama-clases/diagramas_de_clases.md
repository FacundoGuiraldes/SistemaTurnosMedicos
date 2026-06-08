# Diagramas de Clases

* [Diagrama de Clases - Boceto Inicial](./01-boceto-inicial.excalidraw)
* Principios SOLID
  * [Diagrama de Clases - SRP (Single Responsibility Principle)](./01-solid-01-srp.puml)
  * [Diagrama de Clases - OCP (Open/Closed Principle)](./01-solid-02-ocp.puml)
  * [Diagrama de Clases - LSP (Liskov Substitution Principle)](./01-solid-03-lsp.puml)
  * [Diagrama de Clases - ISP (Interface Segregation Principle)](./01-solid-04-isp.puml)
  * [Diagrama de Clases - DIP (Dependency Inversion Principle)](./01-solid-05-dip.puml)

### 2. Diagramas de Clases por Caso de Uso (Módulo Técnico)

| Caso de Uso | Archivo Fuente | Diagrama Renderizado | Descripción |
| :--- | :--- | :--- | :--- |
| **CU1: Registrar Turno** | `01-clases-solicitar-turno.puml` | `01-clases-solicitar-turno.png` | Estructura base orientada a objetos para la gestión e instanciación de turnos médicos (Especialista: Valeria Silva). |
| **CU2: Cancelar turno** | `02-clases-cancelar-turno-02.puml` | `02-clases-cancelar-turno-02.png` | Modelado de clases del flujo de baja de citas, liberación de bloques horarios e inversión de dependencias para alertas. |
| **CU3: Registrar llegada del paciente** | `03-clases-registrar-llegada-03.puml` | `03-clases-registrar-llegada-03.png` | Modelado de clases del flujo de admisión en sala de espera, integrando estados de turnos y acoplamiento abstracto. |