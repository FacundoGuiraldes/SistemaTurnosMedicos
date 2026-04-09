|  |  |  |  |
|---|---|---|---|
| **Nombre de la Clase:** | Sistema | | |
| **Superclase:** | — | | |
| **Subclase:** | — | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Autenticar usuarios | Usuario | Valido credenciales y gestiono el acceso central | usuarioActual: Usuario |
| Registrar paciente | Paciente | Almaceno datos de nuevos pacientes en la base | baseDatos: Database |
| Enviar recordatorios | Paciente, Turno | Notifico automáticamente al paciente sobre su cita | pacientes: List |
| Registrar auditoría | Todos | Anoto quién y cuándo modificó información | historicoModif: List |