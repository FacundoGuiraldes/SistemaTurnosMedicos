|  |  |  |  |
|---|---|---|---|
| **Nombre de la Clase:** | Paciente | | |
| **Superclase:** | Usuario | | |
| **Subclase:** | — | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Proveer datos para la solicitud de turno | Sistema | Soy la entidad que contiene mis antecedentes y datos personales; proveo mi información al Sistema para gestionar mis citas | numeroHistorial: String |
| Notificar intención de cancelación | Sistema | Represento al sujeto de la atención médica y mis datos son consultados para el historial | dni: String |
| Consultar mis turnos programados | Sistema | Puedo visualizar mi agenda personal de salud | dirección: String |
| Registrar mi llegada al consultorio | Sistema, Secretaria | Notifico mi presencia física para que se inicie el flujo de atención | alergias: List<String> |