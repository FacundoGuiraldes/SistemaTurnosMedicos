# Anexo - Introducción al Diseño Orientado a Objetos

## Descripción del paradigma orientado a objetos
La Programación Orientada a Objetos (POO) es un enfoque conceptual que se basa en dividir el programa en modelos de objetos físicos o simulados, en lugar de centrarse únicamente en tareas o procedimientos. Este paradigma se concentra en el objeto tal como lo percibe el usuario, uniendo los datos que lo describen y las operaciones (métodos) que interactúan con dichos datos. Es fundamental porque permite modelar los objetos del mundo real de un modo mucho más eficiente, facilitando la escritura, depuración y el mantenimiento del software a medida que los sistemas crecen en complejidad.

## Los cuatro fundamentos de POO
1. **Abstracción:** Es el proceso de resumir las características de un sistema en sus aspectos esenciales y más relevantes, ignorando los detalles menos importantes. En nuestro proyecto, aplicaríamos la abstracción al definir la clase `Turno`, quedándonos solo con los atributos importantes para el consultorio (fecha, hora, paciente) e ignorando otros datos que no sumen al sistema.
2. **Encapsulamiento y ocultación de datos:** Consiste en combinar en una sola unidad el estado (datos) y el comportamiento (funciones), ocultando la implementación interna del objeto para protegerlo de accesos no autorizados. Por ejemplo, los datos de la clase `Paciente` estarán ocultos y la secretaria solo podrá modificarlos usando métodos específicos habilitados para tal fin.
3. **Herencia:** Es un mecanismo que permite crear nuevas clases (clases derivadas) a partir de clases existentes (clases base), heredando sus propiedades y comportamientos. En el consultorio, podríamos tener una clase base llamada `Persona` de la cual hereden las clases `Paciente` y `Medico`, fomentando la reutilización de código.
4. **Polimorfismo:** Es la capacidad de que objetos de diferentes clases respondan de manera distinta a un mismo mensaje o método. Por ejemplo, si tenemos un método `notificar()`, este podría enviar un recordatorio por WhatsApp si se aplica al `Paciente`, pero enviar un correo electrónico con la agenda del día si se aplica al `Medico`.

## Requisitos iniciales del sistema
Enlace al cuaderno grupal de NotebookLM: https://notebooklm.google.com/notebook/0a9dc1a3-2622-4341-a97a-c1e387c05d93

### Requisitos Funcionales (RF)
* **RF1 Gestión de turnos:** El sistema debe permitirle a la secretaria crear, reprogramar y cancelar los turnos médicos.
* **RF2 Visualizar agenda:** El sistema debe ofrecer la visualización de un calendario u cronograma con la agenda del profesional médico.
* **RF3 Notificar automáticamente al paciente:** El sistema debe enviar recordatorios automáticos a los pacientes el día anterior a su turno médico. El mismo se debe enviar mediante Whatsapp.
* **RF4 Gestión de disponibilidad y bloqueo:** El sistema debe permitir bloquear días y/o horarios dependiendo la disponibilidad del médico, evitando la asignación de turnos en vacaciones, feriados, horarios con compromisos, etc.
* **RF5 Check de asistencia:** El sistema debe permitir marcar con un check los pacientes que efectivamente han asistido a su turno médico, incluyendo hora de llegada y lista de espera.

### Requisitos No Funcionales (RNF)
* **RNF1 Evitar Superposición de turnos:** El sistema debe evitar la superposición de turnos, a menos que se registre un sobreturno de manera manual.
* **RNF2 Simplicidad:** El sistema debe ser simple, evitando complejidades innecesarias.
* **RNF3 Posibilidad de extensión:** El sistema debe permitir que, en un futuro, se agreguen profesionales y se gestionen múltiples salas médicas.
* **RNF4 Historial:** El sistema debe dar acceso a un historial de modificaciones de los turnos, indicando asimismo quien lo ha realizado.
* **RNF5 Tiempo de entrega:** El sistema debe ser funcional para principios de Julio. Prioridad de estabilidad del modelo previo al diseño ideal.

## Casos de Uso y Actores

### Identificar los actores:
* **Usuarios/Secretaria:** Registrar pacientes, asignar turnos, cancelar o modificar turnos, ver y modificar la agenda del doctor. 
* **El doctor:** Ver su agenda, ver quien está esperando en la sala. 
* **Pacientes:** Piden el turno, cancelan o consultan sus turnos.

### Casos de uso posibles

**usuarios:** la secretaria (*registrar pacientes, asignar turnos, cancelar o modificar turnos, ver y modificar la agenda del doctor*). 

El doctor (*ver su agenda, ver quien está esperando en la sala*). 

Pacientes (*piden el turno, cancelan o consulta sus turnos*).

## Casos de uso posibles

**Caso de uso 1: Solicitar turno**

*Actor*: Paciente y secretaria

*Descripción:* Permite al paciente solicitar un turno médico en una fecha disponible mediante la secretaria. 

*Precondición*: El paciente debe estar registrado en el sistema.

*Flujo principal:* 
- El paciente se comunica a la recepción o llama por teléfono. 
- La secretaria ingresa al sistema.
- El sistema muestra los horarios y fechas disponibles.
- El paciente elige una fecha y horario.
- El sistema registra el turno.

*Postcondición:*  el turno queda guardado en la agenda del sistema y bloquea la disponibilidad en la agenda.

**Casos de uso 2: Cancelar turno**

*Actor:* Paciente y secretaria.

*Descripción:* Permite al paciente cancelar un turno previamente asignado.
Precondición: El paciente debe tener un turno asignado.

*Flujo principal:* 
- El paciente se comunica con la secretaria.
- El paciente solicita cancelar su turno.
- El sistema muestra los turnos activos del paciente. 
- El paciente indica el turno que desea cancelar.
- El sistema elimina el turno. 

*Postcondición:* El turno queda disponible nuevamente para otra persona. 

**Casos de uso 3: Registrar llegada del paciente**

*Actor:* Paciente, secretaria y doctor.

*Descripción:* Permite que quede registrado en el sistema quién llegó al lugar y desde qué horario está esperando. 

*Precondición:* El paciente debe haber llegado al consultorio. 

*Flujo principal:* 
- El paciente llega al lugar.
- El paciente informa su llegada a la secretaria.
- La secretaria busca el turno del paciente en el sistema.
- La secretaria registra la llegada del paciente.
- El sistema marca al paciente como “en espera” y registra la hora de llegada.

*Postcondición:* El doctor puede ver quién y desde cuando está esperando a ser atendido. 

**Casos de uso 4: Registrar al paciente**

*Actor:* Paciente y secretaria. 

*Descripción:* Permite que se guarden los datos del paciente en el sistema.

*Precondición:* El paciente debe otorgar sus datos personales. 

*Flujo principal:* 
- El paciente se presenta en el consultorio o se comunica telefónicamente.
- La secretaria solicita los datos personales del paciente.
- El paciente proporciona la información requerida.
- El sistema verifica si el paciente ya existe y en caso contrario, la secretaria ingresa los datos en el sistema.
- El sistema registra y almacena los datos del paciente.

*Postcondición:* El paciente ya puede solicitar turnos. 

**Casos de uso 5: Ver agenda**

*Actor:* Doctor.

*Descripción:* Permite al doctor visualizar su agenda con los turnos programados de un día determinado. 

*Precondición:* Deben existir turnos asignados en la agenda.

*Flujo principal:* 
- El doctor accede al sistema.
- El sistema muestra el menú de opciones disponibles.
- El doctor selecciona la opción “Ver agenda”.
- El doctor selecciona el día que desea consultar.
- El sistema muestra la agenda con los turnos, pacientes y horarios correspondientes.

*Postcondición:* El doctor puede visualizar los turnos programados.   