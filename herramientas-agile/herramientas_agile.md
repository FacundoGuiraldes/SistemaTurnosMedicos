# Índice de Herramientas Agile - Diseño de Clases (A2)

Este apartado contiene la documentación técnica del sistema de gestión de turnos médicos. Se ha utilizado la técnica de **Tarjetas CRC** (Clase-Responsabilidad-Colaborador) para definir la arquitectura del software, sintetizando el modelo en 5 componentes esenciales.

---

## 📂 Tarjetas CRC Principales

Haga clic en cada enlace para ver el detalle de la clase:

1.  **[01 - Usuario (Base de Roles)](./tarjetas-crc/01-tarjeta-crc-usuario.md)**: Define la entidad base y los roles de Paciente, Doctor y Secretaria.
2.  **[02 - Paciente](./tarjetas-crc/02-tarjeta-crc-paciente.md)**: Gestiona la información del paciente y su interacción con las citas.
3.  **[03 - Turno](./tarjetas-crc/03-tarjeta-crc-turno.md)**: La entidad núcleo que representa la reserva médica y su estado.
4.  **[04 - Agenda](./tarjetas-crc/04-tarjeta-crc-agenda.md)**: Orquesta la disponibilidad del profesional y la sala de espera.
5.  **[05 - Sistema (Orquestador)](./tarjetas-crc/05-tarjeta-crc-sistema.md)**: Clase central encargada de las reglas de negocio, persistencia y seguridad.

---

## 📝 Notas de Diseño
* **Abstracción:** Se consolidaron los roles de Doctor y Secretaria dentro de la clase Usuario para optimizar el diseño.
* **Sincronización:** Todas las clases colaboran entre sí para garantizar que no existan superposiciones de horarios (RNF1).