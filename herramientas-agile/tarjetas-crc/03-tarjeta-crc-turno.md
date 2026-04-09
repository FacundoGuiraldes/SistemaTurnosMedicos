|  |  |  |  |
|---|---|---|---|
| **Nombre de la Clase:** | Turno | | |
| **Superclase:** | — | | |
| **Subclase:** | — | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Crear nuevo turno | Sistema, Agenda, Paciente | Represento la reserva de una cita médica | id: String |
| Cancelar turno | Sistema, Agenda, Paciente | Al cancelarme, libero el horario para otro | fecha: Date |
| Validar disponibilidad | Sistema, Agenda | Evito que haya dos pacientes en un mismo horario | hora: Time |
| Registrar asistencia | Sistema, Paciente | Guardo el momento exacto en que llegó el paciente | pacienteId: String |