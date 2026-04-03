# Anexo - Introducción Al Diseño Orientado a Objetos

### Casos de uso
## Identificar los actores:
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
- El sistema muestra los turnos del paciente. 
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
- La secretaria ingresa los datos en el sistema.
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

