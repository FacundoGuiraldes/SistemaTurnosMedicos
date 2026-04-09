|  |  |  |  |
|---|---|---|---|
| **Nombre de la Clase:** | SalaEspera | | |
| **Superclase:** | — | | |
| **Subclase:** | — | | |
| **Responsabilidades** | **Colaboradores** | **Pensamiento del objeto** | **Propiedad** |
| Mantener el orden de llegada (FIFO) | Secretaria, Turno | Manejo la cola física de forma virtual para el doctor | pacientes: List<Paciente> |
| Gestionar estados de espera | Secretaria, Turno | Conozco si cada paciente está Esperando, En consulta o Finalizado | estadoPaciente (Map) |
| Proveer lista de espera actualizada | Doctor, Sistema | Informo al doctor quién es el siguiente paciente a llamar | horaLlegada (Map) |
| Registrar fin de ciclo de espera | Doctor | Remuevo al paciente de la cola una vez terminada la atención | ordenFila (List) |