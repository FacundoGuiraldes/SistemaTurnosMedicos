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

## 6. Pseudocódigo Orientado a Objetos
A continuación se detalla la especificación algorítmica completa que modela la colaboración entre los objetos de dominio, asegurando la trazabilidad con el diagrama de secuencia del CU2 y la eliminación de identificadores relacionales:

```text
Clase InterfazSecretaria {
    Metodo solicitarCancelacion(turno: Turno, motivo: String) {
        // Inicializa el flujo enviando las entidades de dominio correspondientes
        ControladorAgenda.cancelarTurno(turno, motivo)
    }
    
    Metodo mostrarConfirmacion(mensaje: String) {
        Imprimir(mensaje)
    }
}

Clase ControladorAgenda {
    Metodo cancelarTurno(turno: Turno, motivo: String) {
        Si (turno == Nulo) {
            Excepcion("La instancia del turno provista no es válida.")
            Retornar Falso
        }
        
        // 1. Delegación directa sobre los objetos de dominio involucrados según el diagrama de secuencia
        Paciente pacienteAsociado = turno.getPaciente()
        Agenda agendaAsociada = turno.getAgenda()
        
        // 2. Modificación del estado interno de la entidad de negocio (SRP)
        turno.cambiarEstadoACancelado(motivo)
        
        // 3. Colaboración con la Agenda para liberar el bloque horario
        Si (agendaAsociada != Nulo) {
            agendaAsociada.removerTurno(turno)
        } Sino {
            Imprimir("Advertencia: No se detectó una agenda vinculada a la instancia del turno.")
        }
        
        // 4. Despacho de la notificación interactuando con la entidad Paciente
        String detalleMensaje = "Notificación formal: El turno médico ha sido cancelado exitosamente. Motivo: " + motivo
        pacienteAsociado.recibirNotificacion(detalleMensaje)
        
        // 5. Cierre del ciclo de vida de la interacción informando a la vista
        InterfazSecretaria.mostrarConfirmacion("El turno fue cancelado y procesado correctamente por el sistema.")
        
        Retornar Verdadero
    }
}