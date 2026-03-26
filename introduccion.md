# Anexo - Introducción Al Diseño Orientado a Objetos

### Casos de uso
## Identificar los actores:
**usuarios:** la secretaria (*registrar pacientes, asignar turnos, cancelar o modificar turnos, ver y modificar la agenda del doctor*). 

El doctor (*ver su agenda, ver quien está esperando en la sala*). 

Pacientes (*piden el turno, cancelan o consulta sus turnos*).

## Casos de uso posibles

**Caso de uso 1: Solicitar turno**

*Actor*: Paciente y secretaria

*Descripción:* Permite al paciente solicitar un turno médico en una fecha disponible mediante la recepcionista. 

*Precondición*: El paciente debe estar registrado en el sistema.

*Flujo principal:* 
- La recepcionista ingresa al sistema.
- El sistema muestra los horarios y fechas disponibles.
- El paciente elige una fecha y horario.
- El sistema registra el turno.

*Postcondición:*  el turno queda guardado en la agenda del sistema y bloquea la disponibilidad en la agenda.

**Casos de uso 2: Cancelar turno**

*Actor:* Paciente y secretaria.

*Descripción:* Permite al paciente cancelar un turno previamente asignado.
Precondición: El paciente debe tener un turno asignado.

*Flujo principal:* 
- El paciente consulta sus turnos. 
- El paciente indica el turno que desea cancelar.
- El sistema elimina el turno. 

*Postcondición:* El turno queda disponible nuevamente para otra persona. 

**Casos de uso 3: Registrar llegada del paciente**

*Actor:* Paciente, recepcionista y doctor.

*Descripción:* Permite que quede registrado en el sistema quién llegó al lugar y desde qué horario está esperando. 

*Precondición:* El paciente debe haber llegado al consultorio. 

*Flujo principal:* 
- El paciente llega a la sala de espera.
- La secretaria recepciona al paciente en el sistema.
- El sistema indica que el paciente está esperando e indica la hora exacta. 

*Postcondición:* El doctor puede ver quién y desde cuando está esperando a ser atendido. 

**Casos de uso 4: Registrar al paciente**

*Actor:* Paciente y secretaria. 

*Descripción:* Permite que se guarden los datos del paciente en el sistema.

*Precondición:* El paciente debe otorgar sus datos personales. 

*Flujo principal:* 
- El paciente llega o se comunica telefónicamente. 
- La secretaria le pide los datos necesarios.
- El sistema guarda los datos. 

*Postcondición:* El paciente ya puede solicitar turnos. 

**Casos de uso 5: Ver agenda**

*Actor:* Doctor.

*Descripción:* Permite al doctor visualizar su agenda con los turnos programados de un día determinado. 

*Precondición:* Deben existir turnos asignados en la agenda.

*Flujo principal:* 
- El doctor accede al sistema.
- Selecciona la opción de Ver agenda.
- El sistema muestra la agenda del día con los pacientes y horarios de atención. 

*Postcondición:* El doctor puede visualizar los turnos programados.   

