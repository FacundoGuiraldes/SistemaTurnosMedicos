|  |  |  |  |
|---|---|---|---|
| **Nombre de la Clase:** | Usuario | | |
| **Superclase:** | — | | |
| **Subclase:** | Paciente, Secretaria, Doctor | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Autenticarse en el sistema | Sistema | Soy la base común que define acceso y datos personales de cualquier usuario | id: String |
| Cerrar sesión | Sistema | Represento al actor que usa el sistema y necesito gestionar sesión y perfil | nombre: String |
| Modificar perfil personal | Sistema | Centralizo datos comunes y facilito la herencia a los tres roles | email: String |
| | | | teléfono: String |