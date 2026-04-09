|  |  |  |  |
|---|---|---|---|
| **Nombre de la Clase:** | Turno | | |
| **Superclase:** | — | | |
| **Subclase:** | — | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Crear reserva de cita médica | Sistema, Agenda, Paciente | Soy la unidad de cita que vincula paciente, doctor y horario | id, fecha, hora |
| Mantener ciclo de vida de la cita | Sistema, Agenda, Secretaria | Sé si estoy pendiente, cancelado, presente o finalizado | estado, especialidad |
| Actualizar estado por llegada | Secretaria, SalaEspera | Cambio mi estado a "Presente" cuando la secretaria registra la llegada | motivoConsulta |
| Almacenar datos de especialidad | Sistema, Agenda | Permito que el sistema me filtre por especialidad médica | pacienteId, doctorId |
| | | | duracion, sobreturno |