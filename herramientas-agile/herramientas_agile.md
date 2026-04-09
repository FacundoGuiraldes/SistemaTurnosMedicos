# Índice de Herramientas Agile - Diseño de Clases (A2)

Este apartado contiene la documentación técnica detallada del sistema de gestión de turnos médicos. Se ha utilizado la técnica de **Tarjetas CRC** (Clase-Responsabilidad-Colaborador) para definir una arquitectura robusta, escalable y desacoplada, organizada en 8 componentes clave.

---

## 📂 Tarjetas CRC (Arquitectura de 8 Clases)

Haga clic en cada enlace para ver el detalle técnico de la clase:

1.  **[01 - Usuario (Abstracta)](./tarjetas-crc/01-tarjeta-crc-usuario.md)**: Clase base que centraliza la autenticación y datos comunes de todos los actores.
2.  **[02 - Paciente](./tarjetas-crc/02-tarjeta-crc-paciente.md)**: Entidad que provee información personal y médica para la gestión de su salud.
3.  **[03 - Secretaria](./tarjetas-crc/03-tarjeta-crc-secretaria.md)**: Ejecutora operativa encargada de la logística de turnos y recepción física.
4.  **[04 - Doctor](./tarjetas-crc/04-tarjeta-crc-doctor.md)**: Profesional médico que gestiona su agenda diaria y la atención en consulta.
5.  **[05 - Turno](./tarjetas-crc/05-tarjeta-crc-turno.md)**: El núcleo del sistema que vincula paciente, doctor y especialidad en un ciclo de vida definido.
6.  **[06 - Agenda](./tarjetas-crc/06-tarjeta-crc-agenda.md)**: Administradora de las reglas de disponibilidad y franjas horarias de los profesionales.
7.  **[07 - Sala de Espera](./tarjetas-crc/07-tarjeta-crc-sala-espera.md)**: Gestiona el flujo dinámico de pacientes en orden FIFO y sus estados de atención.
8.  **[08 - Sistema (Orquestador)](./tarjetas-crc/08-tarjeta-crc-sistema.md)**: Motor central que coordina las reglas de negocio y delega servicios externos.

---

## 📝 Notas de Diseño Final
* **Especialización:** Se separaron las responsabilidades de Doctor, Secretaria y Paciente para cumplir con el principio de Responsabilidad Única (SOLID).
* **Desacoplamiento:** El Sistema delega la persistencia y notificaciones a servicios especializados, evitando el antipatrón de "Objeto Todopoderoso".
* **Gestión de Estados:** Se introdujo un control preciso sobre el estado del Paciente (Esperando, En consulta, Finalizado) para optimizar la trazabilidad.