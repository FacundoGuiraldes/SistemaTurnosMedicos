# Registro de uso de IA - Especialista ISP

**Prompt utilizado:**
> "Por favor, lee los siguientes archivos de mi espacio de trabajo como contexto: `anexos/introduccion.md`, el diagrama `diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw` y las tarjetas CRC que están dentro de la carpeta `herramientas-agile/tarjetas-crc/`. 
> Analiza el diseño de clases actual del Sistema de Turnos Médicos y realiza lo siguiente:
> 1. Identifica las responsabilidades en las clases actuales que podrían abstraerse en interfaces cohesivas y especializadas.
> 2. Detecta si existen posibles "interfaces gordas" en el diseño actual que obligarían a las clases a implementar métodos que no van a utilizar.
> 3. Propón una refactorización aplicando el Principio de Segregación de Interfaces (ISP), asegurándote de que cada interfaz propuesta sea específica al dominio médico."

**Archivos de contexto referenciados:**
- `anexos/introduccion.md`
- `diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw`
- `herramientas-agile/tarjetas-crc/` (Tarjetas de Usuario, Paciente, Secretaria, Doctor, Turno, Agenda, SalaEspera, etc.)

**Output obtenido:**

*Análisis del Diseño de Clases y Aplicación del Principio de Segregación de Interfaces (ISP)*

La IA identificó problemas de "interfaces gordas" potenciales en clases como Secretaria, Doctor y Agenda, las cuales actualmente poseen responsabilidades mixtas. 
Propuso la siguiente refactorización con interfaces especializadas del dominio médico:

1. `IAgendaMedica`: Para visualización de agendas (Clientes: Doctor, Paciente).
2. `IGestorTurnos`: Para operaciones CRUD de turnos (Clientes: Secretaria, Sistema).
3. `IValidadorDisponibilidad`: Para validación de horarios (Clientes: Agenda, Sistema).
4. `IGestorSalaEspera`: Para gestión de pacientes en espera (Clientes: Doctor, Secretaria).
5. `IRegistradorAsistencia`: Para registro de llegada (Clientes: Secretaria, LlegadaPaciente).
6. `IHistorialClinico`: Para registro de diagnósticos (Clientes: Doctor, Sistema).
7. `IBloqueoAgenda`: Para gestión de disponibilidades (Clientes: Secretaria, Doctor).
8. `IAutorizadorEspecial`: Para autorización de sobreturnos (Clientes: Doctor, Sistema).

La IA destacó que esto asegura una Cohesión Alta, un Acoplamiento Bajo y evita que clases como el Doctor deban implementar métodos administrativos de turnos que no utilizan.

**Ajustes realizados:**
El análisis proporcionado por Copilot fue muy certero. Se validaron las interfaces sugeridas (`IAgendaMedica`, `IGestorTurnos`, `IGestorSalaEspera`, `IHistorialClinico`) asegurando que sus responsabilidades fueran atómicas y los nombres no fueran genéricos, ciñéndose al dominio de turnos médicos. Se rechazó la oferta de la IA de generar automáticamente los archivos de código en el proyecto, ya que el alcance de este parcial es el modelado y la justificación teórica. Se procedió a trasladar su propuesta de relaciones a un diagrama PlantUML normalizado.
