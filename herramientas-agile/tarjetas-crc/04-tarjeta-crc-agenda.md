|  |  |  |  |
|---|---|---|---|
| **Nombre de la Clase:** | Agenda | | |
| **Superclase:** | — | | |
| **Subclase:** | — | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Organizar turnos del día | Sistema, Turno, Paciente | Organizo cronológicamente las citas del doctor | doctorId: String |
| Bloquear horarios | Sistema, Doctor | Impido la creación de turnos en feriados o vacaciones | turnos: List |
| Mostrar cola de espera | Sistema, Paciente | Organizo quién está en sala de espera en orden FIFO | horariosBloqueados: List |
| Obtener disponibilidad | Sistema, Paciente | Sugiero el primer espacio libre para agendar | pacientesEsperando: List |