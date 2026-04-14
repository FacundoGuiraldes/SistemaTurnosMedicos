# Índice de Herramientas Agile - Diseño de Clases (A2)

Este apartado contiene la documentación técnica detallada del sistema de gestión de turnos médicos. Se ha utilizado la técnica de **Tarjetas CRC** (Clase-Responsabilidad-Colaborador) para definir una arquitectura robusta, escalable y desacoplada, organizada en 8 componentes clave.

---

## 📂 Tarjetas CRC (Arquitectura de 8 Clases)

Haga clic en cada enlace para ver el detalle técnico de la clase:

1.  **[01 - Usuario (Abstracta)](./tarjetas-crc/01-tarjeta-crc-usuario.md)**: Clase base que centraliza la autenticación y los datos comunes de todos los actores del sistema.
2.  **[02 - Paciente](./tarjetas-crc/02-tarjeta-crc-paciente.md)**: Actor principal que solicita y gestiona activamente sus turnos y cancelaciones.
3.  **[03 - Secretaria](./tarjetas-crc/03-tarjeta-crc-secretaria.md)**: Ejecutora operativa encargada de la logística de turnos, gestión de departamentos y visualización de agendas.
4.  **[04 - Doctor](./tarjetas-crc/04-tarjeta-crc-doctor.md)**: Profesional médico que gestiona su disponibilidad y registra los diagnósticos de las consultas atendidas.
5.  **[05 - Turno](./tarjetas-crc/05-tarjeta-crc-turno.md)**: Entidad núcleo que vincula paciente y profesional, proveyendo los detalles y estados de cada cita.
6.  **[06 - Agenda](./tarjetas-crc/06-tarjeta-crc-agenda.md)**: Administradora de las reglas de disponibilidad, bloqueos y franjas horarias de los profesionales.
7.  **[07 - Sala de Espera](./tarjetas-crc/07-tarjeta-crc-sala-espera.md)**: Gestiona la recepción activa y el flujo dinámico de pacientes en orden FIFO (cola de espera).
8.  **[08 - Sistema (Orquestador)](./tarjetas-crc/08-tarjeta-crc-sistema.md)**: Motor central que gestiona las colecciones globales, la autenticación y el envío de notificaciones automáticas (RF3).

---

## 📝 Notas de Diseño Final
* **Especialización:** Se separaron las responsabilidades de Doctor, Secretaria y Paciente para cumplir con el principio de Responsabilidad Única (SOLID).
* **Desacoplamiento:** El Sistema delega la persistencia y notificaciones a servicios especializados, evitando el antipatrón de "Objeto Todopoderoso".
* **Consistencia Técnica:** Todas las responsabilidades han sido redactadas en formato activo para reflejar el comportamiento dinámico de los objetos en cumplimiento con los Requerimientos Funcionales (RF1-RF5).