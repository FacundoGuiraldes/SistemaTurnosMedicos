# Pseudocódigo - Happy Path Global del Sistema

---

## 1. Escenario Elegido

**Escenario:** Reserva de turno por especialidad, verificación de disponibilidad, confirmación con notificación y gestión de llegada hasta sala de espera.

**Casos de uso involucrados:** CU1 Solicitar Turno, CU2 Cancelar Turno, CU3 Registrar Llegada, CU4 Registrar Paciente, CU5 Ver Agenda

**Clases participantes:**

- Paciente
- Doctor
- Secretaria
- Turno
- Agenda
- Sistema
- ServicioNotificaciones
- SalaEspera
- LlegadaPaciente
- Especialidad

---

## 2. Pseudocódigo

```text
INICIO Sistema de Turnos Médicos - Happy Path Global

// ============================================================
// CU5: inicialización y verificación de la agenda del doctor
// ============================================================

doctor1 = nuevo Doctor()
doctor1.numeroLicencia = "DRM-2026-001"
doctor1.especialidad = nueva Especialidad("Cardiología", "Atención cardiovascular")
doctor1.consultorio = "Consultorio 5"
doctor1.horariosDisponibles = ["09:00", "09:30", "10:00", "10:30"]

agenda1 = nueva Agenda()
agenda1.doctorId = doctor1.numeroLicencia
agenda1.fecha = hoy()
agenda1.horaApertura = "09:00"
agenda1.horaCierre = "18:00"
agenda1.horariosBloqueados = []
agenda1.estado = EstadoAgenda.Activa

sistema = nuevo Sistema()
sistema.servicioAutenticacion = nuevo ServicioAutenticacion()
sistema.servicioNotificaciones = nuevo ServicioNotificaciones()
sistema.persistenciaService = nuevo PersistenciaService()
sistema.auditoriaService = nuevo AuditoriaService()
sistema.agendas = [agenda1]
sistema.turnos = []

// El sistema consulta el estado de la agenda y sugiere franjas libres
turnosDelDoctor = doctor1.verAgenda(agenda1.fecha)
disponibilidad = agenda1.sugerirProximasFranjasLibres(agenda1.fecha)
si disponibilidad.empty() entonces
    registrar("No hay franjas libres para el doctor")
sino
    registrar("Agenda válida con franjas disponibles")
fin si

// ============================================================
// CU4: registro de nuevo paciente en el sistema
// ============================================================

secretaria1 = nueva Secretaria()
secretaria1.departamento = "Administración"
datosPersonales = secretaria1.solicitarDatosPersonales()
esValido = secretaria1.validarDatos(datosPersonales)

si esValido entonces
    sistema.seleccionarRegistrarPaciente()
    esDuplicado = sistema.validarDuplicidad(datosPersonales["dni"])
    si no esDuplicado entonces
        paciente1 = sistema.registrarPaciente(datosPersonales)
        usuarioCreado = sistema.crearCuentaUsuario(datosPersonales)
        sistema.guardarCambios()
        registrar("Paciente registrado exitosamente")
    sino
        registrar("Paciente ya existe en el sistema")
    fin si
sino
    registrar("Datos inválidos, no se puede registrar el paciente")
fin si

// ============================================================
// CU1: búsqueda de turno por especialidad y selección de franja
// ============================================================

resultados = agenda1.obtenerTurnosDelDia(agenda1.fecha)
turnoSeleccionado = null
para cada turno in resultados hacer
    si turno.especialidad.nombre == doctor1.especialidad.nombre entonces
        turnoSeleccionado = turno
        salir
    fin si
fin para

si turnoSeleccionado == null entonces
    opciones = agenda1.sugerirProximasFranjasLibres(agenda1.fecha)
    turnoSeleccionado = nuevo Turno()
    turnoSeleccionado.fecha = agenda1.fecha
    turnoSeleccionado.hora = opciones[0]
    turnoSeleccionado.especialidad = doctor1.especialidad
fin si

// ============================================================
// CU1: reserva de turno y validación de colisión
// ============================================================

turnoTemporal = nuevo Turno()
turnoTemporal.fecha = agenda1.fecha
turnoTemporal.hora = turnoSeleccionado.hora
turnoTemporal.pacienteId = paciente1.numeroHistorial
turnoTemporal.doctorId = doctor1.numeroLicencia
turnoTemporal.especialidad = doctor1.especialidad
turnoTemporal.estado = EstadoTurno.Disponible

si sistema.validarColisionTurno(turnoTemporal) entonces
    turnoReservado = sistema.solicitarTurno(agenda1.fecha, turnoTemporal.hora, paciente1, doctor1.especialidad)
    agenda1.agregarTurno(turnoReservado)
    sistema.turnos.agregar(turnoReservado)
    sistema.guardarCambios()
    registrar("Turno reservado y persistido en el sistema")
sino
    registrar("Conflicto detectado: no se puede reservar el turno")
    detenerFlujo()
fin si

// ============================================================
// CU1: envío de notificación de confirmación
// ============================================================

notificacion1 = nueva Notificacion()
notificacion1.mensaje = "Su turno ha sido reservado."
notificacion1.destinatario = paciente1.email
notificacion1.tipo = "Confirmacion"
sistema.enviarRecordatorioAutomatico(paciente1, turnoReservado)
sistema.servicioNotificaciones.enviarNotificacion(paciente1, notificacion1.mensaje)
notificacion1.enviar()

// ============================================================
// CU3: llegada del paciente y paso a sala de espera
// ============================================================

llegada = paciente1.registrarLlegada()
si llegada.validarTurnoExistente(paciente1) entonces
    llegada.notificarIngresoASalaDeEspera(nueva SalaEspera())
    turnoReservado.marcarEnEspera()
    registrar("Paciente en sala de espera listo para atención")
sino
    sistema.cancelarTurno(turnoReservado.id, "Llegada inválida o turno no encontrado")
    registrar("Flujo de llegada interrumpido por turno inválido")
fin si

// ============================================================
// CU2: cancelación de turno (flujo alternativo)
// ============================================================

// Si el paciente decide cancelar antes de ser atendido:
// sistema.cancelarTurno(turnoReservado.id, "Cancelación por paciente")
// agenda1.removerTurno(turnoReservado)

FIN
```

---

## 3. Trazabilidad del Pseudocódigo

| Bloque | Caso de uso | Clases involucradas | Diagrama de secuencia de referencia |
|--------|-------------|---------------------|-------------------------------------|
| Inicialización y verificación de agenda | CU5 Ver Agenda | Doctor, Agenda, Sistema | [Ver Agenda](../../diagramas/05-diagramas-secuencia/05-secuencia-ver-agenda-ver-agenda-exitoso-05.png) |
| Registro de nuevo paciente | CU4 Registrar Paciente | Secretaria, Sistema, Paciente | [Registrar Paciente](../../diagramas/05-diagramas-secuencia/05-secuencia-registrar-paciente-registrar-paciente-04.png) |
| Búsqueda y selección de turno | CU1 Solicitar Turno | Paciente, Doctor, Agenda, Turno | [Solicitar Turno](../../diagramas/05-diagramas-secuencia/05-secuencia-solicitar-turno-solicitar-turno-01.png) |
| Reserva y validación de colisión | CU1 Solicitar Turno | Sistema, Agenda, Turno, Paciente | [Solicitar Turno](../../diagramas/05-diagramas-secuencia/05-secuencia-solicitar-turno-solicitar-turno-01.png) |
| Envío de notificación de confirmación | CU1 Solicitar Turno | Sistema, ServicioNotificaciones, Paciente, Notificacion | [Solicitar Turno](../../diagramas/05-diagramas-secuencia/05-secuencia-solicitar-turno-solicitar-turno-01.png) |
| Registro de llegada y sala de espera | CU3 Registrar Llegada | Paciente, LlegadaPaciente, SalaEspera, Turno | [Registrar Llegada](../../diagramas/05-diagramas-secuencia/05-secuencia-registrar-llegada-registrar-llegada-del-paciente-03.png) |
| Cancelación de turno (alternativo) | CU2 Cancelar Turno | Sistema, Agenda, Turno | [Cancelar Turno](../../diagramas/05-diagramas-secuencia/05-secuencia-cancelar-turno-cancelar-turno-02.png) |