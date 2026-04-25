# Principio de Responsabilidad Única (SRP)

## Propósito y Tipo del Principio SOLID:

SRP busca que una clase tenga una única responsabilidad. Esto mejora el mantenimiento, la claridad del diseño y reduce el acoplamiento.

## Motivación

En el diseño inicial del sistema de turnos médicos se identificaron clases que presentan múltiples responsabilidades, lo cual dificulta su mantenimiento y evolución. A continuación se analizan tres clases principales:

### CLASE 1: `Sistema` - El "God Object"

La clase Sistema concentra múltiples responsabilidades, ya que se encarga de coordinar la lógica de negocio, validar turnos, autenticar usuarios y enviar notificaciones. Esto genera un alto acoplamiento y hace que cualquier cambio en una de estas funcionalidades obligue a modificar la misma clase.

Para aplicar SRP, se propone separar estas responsabilidades en clases específicas como ValidadorTurnos, ServicioAutenticacion y ServicioNotificaciones, dejando a Sistema únicamente como orquestador del flujo principal del sistema. 

---
### CLASE 2: `Turno` - 

La clase Turno también presenta múltiples responsabilidades, ya que además de almacenar los datos del turno, gestiona su ciclo de vida y las transiciones de estado (por ejemplo, pendiente, confirmado o cancelado).

Esto complica el mantenimiento, ya que cualquier cambio en las reglas de estado afecta directamente a la clase.

Para aplicar SRP, se propone dividirla en DatosTurno, encargada de almacenar la información, y GestorEstadoTurno, responsable de manejar los cambios de estado.

---
### CLASE 3: `Paciente` - 

La clase Paciente mezcla responsabilidades de datos y lógica de negocio. Por un lado, almacena información personal del paciente, y por otro, gestiona acciones como solicitar turnos, cancelarlos o registrar la llegada.

Esto genera problemas de reutilización y mantenimiento, ya que cambios en la lógica de negocio afectan a una clase que también representa datos.

Para aplicar SRP, se propone separar estas responsabilidades en una clase DatosPaciente, encargada únicamente de los datos, y otras clases como GestorSolicitudTurnos y GestorCancelacionTurnos, encargadas de la lógica de negocio.

## Estructura de Clases

A continuación se presenta el diagrama UML que muestra la refactorización propuesta aplicando el principio SRP.
* [Diagrama de Clases SRP](../../diagramas/01-diagrama-clases/01-solid-01-srp.png)

## Justificación Técnica

En el diagrama UML se puede observar cómo las responsabilidades fueron separadas en distintas clases, cada una con una única función específica.

La clase Sistema queda como orquestadora del flujo principal, mientras que las validaciones, autenticación y notificaciones se delegan en clases independientes. De la misma manera, Paciente y Turno se dividen en clases de datos y clases encargadas de la lógica de negocio.

Esta separación permite que cada clase tenga una única razón para cambiar, facilitando el mantenimiento, mejorando la claridad del diseño y reduciendo el acoplamiento entre componentes del sistema.