|  |  |  |  |
|---|---|---|---|
| **Nombre de la Clase:** | Doctor | | |
| **Superclase:** | Usuario | | |
| **Subclase:** | — | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Ver agenda diaria de turnos | Agenda | Soy el profesional que necesita conocer mis citas, tiempos y especialidad | numeroLicencia: String |
| Consultar pacientes en sala de espera | Agenda, SalaEspera | Requiero saber quién está esperando y cuánto tiempo lleva allí | especialidad: String |
| Marcar pacientes atendidos | Turno | Indico cuándo finalizo una consulta para liberar el turno | consultorio: String |
| Definir disponibilidad general | Agenda, Sistema | Establezco mis reglas de horario para que la Agenda las aplique | horariosDisponibles: List<String> |
| Registrar diagnóstico de la consulta | Turno, Sistema | Registro el resultado de la consulta para el historial del paciente | |
| **Autorizar sobreturno en su agenda** | **Agenda, Secretaria** | **Solo yo decido agregar un turno extra; si no estoy presente, no se agrega.** | |