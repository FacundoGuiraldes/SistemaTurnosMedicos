|  |  |  |  |
|---|---|---|---|
| **Nombre de la Clase:** | Sistema | | |
| **Superclase:** | — | | |
| **Subclase:** | — | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Orquestar flujos de negocio | Agenda, Turno, Secretaria | Delego la lógica a las clases expertas y coordino las reglas globales | usuarioActual |
| Validar colisiones de turnos | Turno, Agenda | Verifico que no existan dos turnos para el mismo doctor en el mismo momento | persistenciaService |
| Gestionar servicios externos | PersistenciaService, NotificacionService | Coordino el guardado de datos y el envío de notificaciones | notificacionService |
| Mantener trazabilidad del sistema | AuditoriaService | Registro cada cambio importante para auditoría de seguridad | auditoriaService |
| Autenticar usuarios e iniciar sesión | Usuario | Verifico credenciales y permito acceso al sistema | |
| Enviar recordatorio automático al paciente (RF3) | Paciente, Turno | Envío notificaciones automáticas antes de las citas | |
| | | | usuarios: List<Usuario> |
| | | | turnos: List<Turno> |
| | | | agendas: List<Agenda> |