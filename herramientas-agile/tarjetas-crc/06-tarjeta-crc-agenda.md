|  |  |  |  |
|---|---|---|---|
| **Nombre de la Clase:** | Agenda | | |
| **Superclase:** | — | | |
| **Subclase:** | — | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Configurar reglas de disponibilidad | Doctor, Sistema | Organizo la jornada laboral del doctor y aplico sus restricciones | doctorId: String |
| Gestionar franjas horarias | Sistema, Turno | Administro qué espacios son válidos para nuevos turnos | turnos: List<Turno> |
| Validar turnos contra reglas horarias | Sistema | Verifico si una solicitud de turno entra en el horario permitido del doctor | fecha: Date |
| Sugerir próximas franjas libres | Sistema | Analizo mis huecos vacíos para ofrecer opciones al paciente | horaApertura/Cierre |
| | | | horariosBloqueados |