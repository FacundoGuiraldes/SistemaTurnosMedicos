| | | | |
| :--- | :--- | :--- | :--- |
| **Nombre de la Clase:** | **LlegadaPaciente** | | |
| **Superclase:** | — | | |
| **Subclase:** | — | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedades** |
| Registrar presencia física del paciente | Paciente, Turno | Soy el comprobante de que el paciente ya está en la clínica para su cita. | horaLlegada: DateTime |
| Validar correspondencia con turno | Turno | Verifico que la llegada coincida con un turno previamente asignado. | estadoValidacion: Boolean |
| Notificar ingreso a sala de espera | SalaEspera | Aviso al sistema que el paciente está listo para ser llamado por el doctor. | |