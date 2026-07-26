|  |  |  |  |
|---|---|---|---|
| **Nombre de la Clase:** | Secretaria | | |
| **Superclase:** | Usuario | | |
| **Subclase:** | — | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Registrar nuevo paciente en el sistema | Sistema, Paciente | Soy la ejecutora operativa: ingreso pacientes y gestiono la logística de turnos | departamento: String |
| Crear o modificar turnos | Sistema, Agenda, Turno | Manejo la operación real de agendar consultas según disponibilidad | departamento: String |
| Cancelar turnos y liberar horarios | Sistema, Agenda, Turno | Ejecuto las anulaciones y actualizo el estado del turno | departamento: String |
| Registrar llegada de pacientes | Turno, SalaEspera, Sistema | Centralizo la llegada física y actualizo la sala de espera y el estado del turno | |
| Solicitar bloqueo de horarios del doctor | Sistema, Agenda | Coordino los días no disponibles y delego la regla a la Agenda | |
| Ver y modificar la agenda del doctor | Agenda, Sistema | Gestiono la agenda del doctor para coordinar turnos | |