| | | | |
|---|---|---|---|
| **Nombre de la Clase:** | LlegadaPaciente | | |
| **Superclase:** | — | | |
| **Subclase:** | — | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Registrar presencia física del paciente | Paciente, Secretaria | Valido que la persona esté presente en el centro médico para activar el flujo | horaLlegada: DateTime |
| Validar turno existente | Turno, Sistema | Verifico que el paciente tenga un turno programado para el día y hora actual | estadoValidacion: Boolean |
| Notificar ingreso a sala de espera | SalaEspera | Una vez validado, informo a la sala que el paciente está listo para ser llamado | idTurno: String |
| Gestionar prioridad de atención | Secretaria, SalaEspera | Determino si el paciente tiene alguna prioridad o si el turno es un sobreturno autorizado | prioridad: Boolean |
