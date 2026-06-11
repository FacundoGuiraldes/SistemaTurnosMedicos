# Los Cuatro Pilares del Paradigma Orientado a Objetos

## 1. Encapsulamiento

**Definición:** El encapsulamiento agrupa datos y comportamientos en una unidad y oculta los detalles internos, exponiendo solo una interfaz pública controlada.

**Ejemplo 1 — Paciente:**
La clase `Paciente` oculta atributos sensibles como `- dni: String`, `- direccion: String` y `- alergias: List<String>`. Estos datos no son accesibles directamente desde fuera; las operaciones públicas como `+ solicitarTurno(...)` y `+ cancelarTurno(...)` son las únicas vías previstas para interactuar con el estado del paciente.

![Encapsulamiento - Ejemplo 1](../../diagramas/01-diagrama-clases/capturas-pilares/poo-encapsulamiento-ejemplo-1.png)

**Ejemplo 2 — Turno:**
La clase `Turno` encapsula su ciclo de vida mediante el atributo privado `- estado: EstadoTurno`. El estado solo cambia a través de métodos controlados como `+ eliminarTurno(): void`, `+ marcarEnEspera(): void` y `+ marcarAtendido(): void`, evitando que otras clases modifiquen el estado internamente.

![Encapsulamiento - Ejemplo 2](../../diagramas/01-diagrama-clases/capturas-pilares/poo-encapsulamiento-ejemplo-2.png)

## 2. Herencia

**Definición:** La herencia permite que una subclase reutilice y extienda los datos y comportamientos de una clase base, modelando jerarquías de especialización del dominio.

**Ejemplo 1 — Usuario → Paciente:**
La clase abstracta `Usuario` contiene atributos y métodos comunes como `- id`, `- nombre`, `- email`, `- telefono`, `+ login(...)` y `+ logout()`. `Paciente` hereda esta estructura, evitando duplicar la lógica de identidad y autenticación en cada tipo de usuario.

![Herencia - Ejemplo 1](../../diagramas/01-diagrama-clases/capturas-pilares/poo-herencia-ejemplo-1.png)

**Ejemplo 2 — Usuario → Doctor:**
`Doctor` también hereda de `Usuario`, reutilizando la identidad y los métodos de sesión. A su vez agrega atributos específicos como `- numeroLicencia` y `- especialidad`, lo que representa correctamente la especialización de un médico dentro del dominio.

![Herencia - Ejemplo 2](../../diagramas/01-diagrama-clases/capturas-pilares/poo-herencia-ejemplo-2.png)

## 3. Polimorfismo

**Definición:** El polimorfismo permite que diferentes clases respondan a la misma operación o mensaje con comportamientos adecuados a su tipo concreto.

**Ejemplo 1 — `login(...)` en `Paciente`, `Secretaria` y `Doctor`:**
El método `login(...)` es parte de la abstracción `Usuario` y puede aplicarse a sus subclases. Aunque el diagrama no detalla la implementación específica, el modelo admite que cada tipo de usuario valide credenciales según su rol mientras comparte la misma interfaz de acceso.

![Polimorfismo - Ejemplo 1](../../diagramas/01-diagrama-clases/capturas-pilares/poo-polimorfismo-ejemplo-1.png)

**Ejemplo 2 — `verAgenda(...)` en `Doctor` y `Secretaria`:**
`Doctor` y `Secretaria` realizan la acción de ver agenda con firmas diferentes, pero el dominio mantiene el mismo propósito: consultar disponibilidad y turnos del doctor. Este diseño permite comportamientos diferenciados según el rol que solicita la información.

![Polimorfismo - Ejemplo 2](../../diagramas/01-diagrama-clases/capturas-pilares/poo-polimorfismo-ejemplo-2.png)

## 4. Abstracción

**Definición:** La abstracción selecciona los aspectos esenciales de una entidad y oculta los detalles de implementación irrelevantes para el usuario del objeto.

**Ejemplo 1 — Turno:**
`Turno` modela la cita médica con atributos de negocio clave (`fecha`, `hora`, `pacienteId`, `doctorId`, `estado`) e ignora detalles de infraestructura como persistencia o interfaz de usuario. De este modo, expone una representación simple del dominio de citas.

![Abstracción - Ejemplo 1](../../diagramas/01-diagrama-clases/capturas-pilares/poo-abstraccion-ejemplo-1.png)

**Ejemplo 2 — Sistema:**
La clase `Sistema` abstrae la orquestación del flujo completo del sistema. Expone métodos como `+ solicitarTurno(...)` y `+ enviarRecordatorioAutomatico(...)` sin revelar cómo se gestiona internamente la autenticación, la persistencia o el envío de notificaciones.

![Abstracción - Ejemplo 2](../../diagramas/01-diagrama-clases/capturas-pilares/poo-abstraccion-ejemplo-2.png)
