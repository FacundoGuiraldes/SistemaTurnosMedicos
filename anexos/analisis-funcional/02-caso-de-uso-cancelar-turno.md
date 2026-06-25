# Anexo Funcional: CU2 - Cancelar Turno

## 📌 Datos del Estudiante
- **Nombre y Apellido:** Carola Benvenuto
- **Número de Matrícula:** 158686
- **Carrera:** Tecnicatura Universitaria en Programación de Sistemas
- **Materia:** Diseño Orientado a Objetos
- **Profesor:** Lic. Matías Velasquez
- **Cuatrimestre/Año:** 1º Bimestre / 2026
- **Rol asignado para esta entrega:** Analista Funcional de Casos de Uso 2 y 3

---

## 1. Descripción del Caso de Uso y Trazabilidad
El sistema permite que un Paciente o una Secretaria soliciten la cancelación de una cita médica previamente agendada. El flujo gestiona la baja del registro, revierte la ocupación del bloque horario en la agenda del profesional de la salud y dispara los mecanismos de notificación digital automatizados a los actores involucrados.

### Mapeo de Trazabilidad Explícita:
* **RF-04 (Cancelar Turnos):** Satisfecho mediante el método de orquestación en la controladora del sistema y la mutación de estado en la entidad del dominio.
* **RF-12 (Notificación Automática):** Satisfecho mediante el uso de abstracciones de mensajería inyectadas en el flujo de cancelación.

---

## 2. Diagrama de Casos de Uso (A2)
El comportamiento funcional de este módulo se encuentra tipificado en el modelo general de casos de uso de la Actividad N° 2. 

![Diagrama de Casos de Uso CU2](../../diagramas/02-casos-de-uso/02-caso-uso-cancelar-turno-02/02-caso-uso-cancelar-turno-02.png)

* **Descripción breve:** El diagrama (Ref: image_78a7e4.png) expone que tanto el actor `Paciente` como el actor `Secretaria` pueden iniciar el caso de uso principal `Cancelar turno`. Este último incluye de manera obligatoria (`«include»`) la ejecución secuencial de los subprocesos `Buscar turno`, `Liberar disponibilidad` y `Notificar cancelación`.

---

## 3. Diagrama de Actividades (A3)
El flujo operativo y las bifurcaciones lógicas del proceso de cancelación se encuentran documentados en el artefacto de la Actividad N° 3.

![Diagrama de Actividades CU2](../../diagramas/04-diagramas-actividades/04-actividad-cancelar-turno-02.png)

* **Descripción breve:** El flujo inicia con la recepción del identificador del turno, evalúa la existencia del registro en el repositorio y, ante una resolución positiva, procede en paralelo a modificar el estado de la cita, liberar el bloque de la agenda del médico y despachar la alerta de confirmación.

---

## 4. Diagrama de Secuencia (A3)
La interacción cronológica y el paso de mensajes entre los objetos del sistema durante la ejecución de este caso de uso se detallan a continuación.

![Diagrama de Secuencia CU2](../../diagramas/05-diagramas-secuencia/05-secuencia-cancelar-turno-cancelar-turno-02.png)

* **Descripción breve:** Describe la secuencia de llamadas desde la interfaz de usuario hacia el controlador `Sistema`, el cual invoca secuencialmente al repositorio de datos para recuperar la entidad, ejecuta la cancelación y delega a las interfaces correspondientes la liberación de la agenda y el envío de notificaciones.

---

## 5. Diagrama de Clases Parcial y Relaciones UML
El diseño estructural específico para dar soporte a este comportamiento se encuentra implementado bajo principios SOLID en el archivo `02-clases-cancelar-turno-02.puml`.

![Diagrama de Clases CU2](../../diagramas/01-diagrama-clases/02-clases-cancelar-turno-02.png)

### Clases involucradas:
| Clase | Responsabilidad (según tarjeta CRC) | Tarjeta CRC |
|-------|-------------------------------------|-------------|
| **InterfazSecretaria** | Responsable de interactuar con el personal administrativo para notificar y renderizar los eventos de atención al paciente. | [03-tarjeta-crc-secretaria.md](../../herramientas-agile/tarjetas-crc/03-tarjeta-crc-secretaria.md) |
| **ControladorAgenda** | Orquestador encargado de coordinar los mensajes de negocio y las interacciones lógicas entre las entidades del dominio para la gestión de turnos. | [08-tarjeta-crc-sistema.md](../../herramientas-agile/tarjetas-crc/08-tarjeta-crc-sistema.md) |
| **Turno** | Representar la cita médica pactada, controlando sus datos horarios, profesional asignado y sus transiciones de estado de negocio. | [05-tarjeta-crc-turno.md](../../herramientas-agile/tarjetas-crc/05-tarjeta-crc-turno.md) |
| **Agenda** | Administrar los bloques horarios disponibles de los médicos y gestionar la asignación o remoción de turnos asociados. | [06-tarjeta-crc-agenda.md](../../herramientas-agile/tarjetas-crc/06-tarjeta-crc-agenda.md) |
| **Paciente** | Representar al sujeto de atención médica del sistema, almacenando su información personal y vinculación con sus citas. | [02-tarjeta-crc-paciente.md](../../herramientas-agile/tarjetas-crc/02-tarjeta-crc-paciente.md) |

### Tabla de Relaciones Estructurales:
| Origen | Relación UML | Destino | Multiplicidad / Nota |
| :--- | :--- | :--- | :--- |
| `Paciente` | Herencia (`--\|>`) | `Usuario` | Especialización de entidad general. |
| `Secretaria` | Herencia (`--\|>`) | `Usuario` | Especialización de entidad general. |
| `Turno` | Asociación (`-->`) | `Paciente` | 1 a 1 (Un turno pertenece a un paciente). |
| `Turno` | Asociación (`-->`) | `Agenda` | 1 a 1 (Asociado al bloque de la agenda médica). |
| `Sistema` | Asociación (`-->`) | `ITurnoRepository` | Inversión de Dependencias (DIP) mediante inyección. |
| `Sistema` | Asociación (`-->`) | `IAgendaService` | Inversión de Dependencias (DIP) mediante inyección. |
| `Sistema` | Asociación (`-->`) | `INotificacionService` | Inversión de Dependencias (DIP) mediante inyección. |

---

## 6. Pseudocódigo

```text
INICIO Cancelar Turno

// Contexto: El actor Secretaria inicia la interacción en el consultorio médico solicitando la baja de una cita programada.
ControladorAgenda elControlador = Instanciar ControladorAgenda()
InterfazSecretaria laInterfaz = Instanciar InterfazSecretaria()

// Se configuran los enlaces por inyección de referencias entre componentes
laInterfaz.controlador = elControlador
elControlador.interfazUsuario = laInterfaz

// Instanciación inicial de las entidades de dominio necesarias obtenidas en memoria
Turno turnoSeleccionado = laInterfaz.obtenerTurnoSeleccionado()

SI turnoSeleccionado != Nulo
    
    // Qué está resolviendo este bloque: Recuperación del grafo de objetos de dominio vinculados (sin usar IDs)
    Paciente pacienteAsociado = turnoSeleccionado.obtenerInfoPaciente()
    Agenda agendaAsociada = turnoSeleccionado.obtenerAgenda()
    
    // Mutación controlada del estado interno del objeto de negocio (SRP)
    turnoSeleccionado.cambiarEstadoACancelado("Solicitado por el paciente")
    
    // Qué decisión se toma y por qué: Colaboración entre objetos para liberar el bloque horario en la agenda médica
    SI agendaAsociada != Nulo
        agendaAsociada.removerTurno(turnoSeleccionado)
    SINO
        laInterfaz.mostrarAdvertencia("No se detectó una agenda vinculada a la instancia del turno.")
    FIN SI
    
    // Envío de mensaje interactivo hacia la entidad Paciente para despachar la notificación formal
    String detalleMensaje = "Notificación formal: El turno médico ha sido cancelado exitosamente."
    pacienteAsociado.recibirNotificacion(detalleMensaje)
    
    // Qué produce esta acción en el sistema: Cierre de la transacción notificando a la instancia de la vista
    laInterfaz.mostrarConfirmacion("El turno fue cancelado y procesado correctamente por el sistema.")
    
SINO
    laInterfaz.mostrarError("La instancia del turno provista no es válida.")
FIN SI

// Estado final del sistema tras ejecutar el caso de uso
Retornar turnoSeleccionado

FIN