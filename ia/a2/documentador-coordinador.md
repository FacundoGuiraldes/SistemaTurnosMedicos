# Documentación de Code Reviews con Copilot Agent Mode
## Rol: Documentador y Coordinador de Repositorio — Actividad Obligatoria N°2

---

## Contexto general

En cada code review se utilizó **Copilot Agent Mode** en VS Code, proporcionando como contexto principal el archivo `anexos/introduccion.md`, que contiene los requisitos funcionales, no funcionales y los casos de uso definidos en la Actividad Obligatoria N°1. El objetivo de cada revisión fue validar que los entregables de cada integrante fueran coherentes con ese marco de referencia.

El sistema modelado es un **sistema de gestión de turnos para un consultorio médico**, con las siguientes clases definidas en el boceto inicial:
- `Usuario` (abstracta)
- `Paciente` (hereda de Usuario)
- `Secretaria` (hereda de Usuario)
- `Doctor` (hereda de Usuario)
- `Turno`
- `Agenda`
- `SalaEspera`
- `Sistema` (singleton)

Los actores del sistema son: **Paciente**, **Secretaria** y **Doctor**.

Los 5 casos de uso definidos son:
1. Solicitar turno
2. Cancelar turno
3. Registrar llegada del paciente
4. Registrar al paciente
5. Ver agenda

---

## Code Review 1 — PR #26 de carolabenvenuto-uces (Diseñador de Tarjetas CRC)

**PR revisada:** `#26 - A2 - Diseñador de Tarjetas CRC`
**Autora:** carolabenvenuto-uces
**Rol:** Diseñador de Tarjetas CRC

### Prompt utilizado en Copilot Agent Mode

```
Lee el archivo anexos/introduccion.md de este repositorio como contexto del proyecto.
También tomá como referencia el boceto de clases en 
diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw.

El sistema es un gestor de turnos para un consultorio médico. 
Las clases definidas en el boceto inicial son:
- Usuario (abstracta): id, nombre, email, telefono / login(), logout(), modificarPerfil()
- Paciente (hereda de Usuario): numeroHistorial, dni, direccion, alergias / solicitarTurno(), cancelarTurno(), consultarTurnos(), registrarLlegada()
- Secretaria (hereda de Usuario): numeroEmpleado, departamento / registrarPaciente(), asignarTurno(), cancelarTurno(), modificarTurno(), verAgenda()
- Doctor (hereda de Usuario): numeroLicencia, especialidad, consultorio / verAgenda(), verPacientesEsperando(), registrarDiagnostico()
- Turno: id, fecha, hora, estado, motivoConsulta, pacienteId, doctorId / crear(), cancelar(), modificar(), getDetalles()
- Agenda: doctor, turnos, fecha / agregarTurno(), eliminarTurno(), obtenerTurnosDelDia()
- SalaEspera: pacientes, horaLlegada / registrarLlegada(), obtenerPacientesEsperando(), removerPaciente()
- Sistema (singleton): usuarios, turnos, agendas / iniciar(), autenticar(), gestionarTurnos()

Revisá los archivos de tarjetas CRC agregados en esta PR, ubicados en 
herramientas-agile/tarjetas-crc/.

Validá que cada tarjeta sea coherente con:
- Los requisitos funcionales RF1 a RF5 definidos en introduccion.md
- Los 5 casos de uso documentados (Solicitar turno, Cancelar turno, Registrar llegada, Registrar paciente, Ver agenda)
- El boceto de clases

Para cada tarjeta, verificá que contenga todos los campos requeridos:
nombre de la clase, superclase/subclase (si aplica), pensamiento del objeto,
responsabilidades principales, colaboraciones con otras clases y propiedad.

Indicame:
1. ¿Las responsabilidades de cada clase son consistentes con los requisitos funcionales?
2. ¿Las colaboraciones entre clases reflejan correctamente los casos de uso?
3. ¿La herencia entre Usuario, Paciente, Secretaria y Doctor está correctamente representada?
4. ¿Falta algún campo requerido en alguna tarjeta?
5. ¿Qué cambios concretos sugerís, indicando archivo y línea?

Publica los comentarios directamente en la Pull Request en las líneas correspondientes

No respondas el chat salvo para el resumen final
```

### Archivos de contexto referenciados

- `anexos/introduccion.md`
- `diagramas/01-diagrama-clases/01-boceto-inicial.excalidraw`
- `herramientas-agile/tarjetas-crc/*.md` (archivos de la PR)

### Output de Copilot (resumen)

Copilot analizó las 8 tarjetas CRC contra el boceto inicial, los RF1–RF5 y los 5 casos de uso. Resultados:

**Campos requeridos:** todas las tarjetas los contienen completos. ✅

**Herencia (Usuario → Paciente / Secretaria / Doctor):** correctamente representada. ✅

**Cobertura de requisitos funcionales:**

| RF | Estado |
|---|---|
| RF1 — Gestión de turnos | ✅ Cubierto por Secretaria + Turno |
| RF2 — Visualizar agenda | ✅ Cubierto por Agenda + Doctor |
| RF3 — Notificación automática (WhatsApp) | ⚠️ Solo cubierto implícitamente vía `NotificacionService` en Sistema |
| RF4 — Disponibilidad y bloqueo | ✅ Cubierto por Agenda + Doctor |
| RF5 — Check de asistencia | ✅ Cubierto por SalaEspera + Secretaria + Turno |

**Problemas detectados:**

1. **`01-tarjeta-crc-usuario.md`** — La clase `Usuario` es abstracta en el boceto, pero la tarjeta no lo indica en ningún campo.
2. **`02-tarjeta-crc-paciente.md`** — Las responsabilidades `solicitarTurno()` y `cancelarTurno()` se redactaron de forma pasiva en lugar de activa. Colaboradores de CU1 y CU2 incompletos: faltan `Turno` y `Agenda`.
3. **`03-tarjeta-crc-secretaria.md`** — La propiedad `consultorio` pertenece a `Doctor` en el boceto, no a Secretaria. `turnoLaboral` no está definida en el boceto. Falta la propiedad `departamento`. Falta la responsabilidad `verAgenda()`.
4. **`04-tarjeta-crc-doctor.md`** — Falta la responsabilidad `registrarDiagnostico()` definida en el boceto.
5. **`05-tarjeta-crc-turno.md`** — "Almacenar datos de especialidad" describe una propiedad, no un comportamiento (responsabilidad mal redactada).
6. **`07-tarjeta-crc-sala-espera.md`** — Falta `registrarLlegada()` como responsabilidad activa de SalaEspera (sí está en el boceto).
7. **`08-tarjeta-crc-sistema.md`** — Faltan las propiedades colectivas `usuarios`, `turnos`, `agendas` del boceto. Falta la responsabilidad `autenticar()` con colaborador `Usuario`. RF3 no está representado como responsabilidad explícita.

### Ajustes realizados al output de la IA

Todos los comentarios generados por Copilot fueron revisados y considerados pertinentes. Se publicaron íntegramente en la PR sin modificaciones.

- ✅ Observación sobre clase abstracta `Usuario` — aceptada, es una omisión clara respecto al boceto.
- ✅ Responsabilidades pasivas en `Paciente` — aceptada, el boceto define métodos activos.
- ✅ Propiedades incorrectas en `Secretaria` (`consultorio`, `turnoLaboral`) — aceptada, son discrepancias directas con el boceto.
- ✅ `registrarDiagnostico()` faltante en `Doctor` — aceptada, método explícito en el boceto.
- ✅ Responsabilidad mal redactada en `Turno` — aceptada, una responsabilidad debe ser un comportamiento, no un atributo.
- ✅ `registrarLlegada()` faltante en `SalaEspera` — aceptada, método explícito en el boceto.
- ✅ Propiedades y responsabilidades faltantes en `Sistema` — aceptada, el boceto las define como parte del singleton.
- ✅ RF3 sin cobertura explícita — aceptada, ninguna tarjeta lo menciona.

### Request Changes cargados en el diff de la PR

| Archivo | Cambio sugerido |
|---|---|
| `herramientas-agile/tarjetas-crc/01-tarjeta-crc-usuario.md` | Agregar campo `Abstracta: Sí` |
| `herramientas-agile/tarjetas-crc/02-tarjeta-crc-paciente.md` | Reescribir responsabilidades `solicitarTurno()` y `cancelarTurno()` de forma activa; agregar `Turno` y `Agenda` como colaboradores |
| `herramientas-agile/tarjetas-crc/03-tarjeta-crc-secretaria.md` | Reemplazar `turnoLaboral` y `consultorio` por `departamento`; agregar responsabilidad `verAgenda()` |
| `herramientas-agile/tarjetas-crc/04-tarjeta-crc-doctor.md` | Agregar responsabilidad `registrarDiagnostico()` |
| `herramientas-agile/tarjetas-crc/05-tarjeta-crc-turno.md` | Reescribir "Almacenar datos de especialidad" como comportamiento activo (`getDetalles()`) |
| `herramientas-agile/tarjetas-crc/07-tarjeta-crc-sala-espera.md` | Agregar responsabilidad `registrarLlegada()` como recepción activa del paciente |
| `herramientas-agile/tarjetas-crc/08-tarjeta-crc-sistema.md` | Agregar propiedades `usuarios`, `turnos`, `agendas`; agregar responsabilidad `autenticar()` con colaborador `Usuario`; cubrir RF3 explícitamente |

**Review publicada:** https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/26#pullrequestreview-4095848222

---

## Code Review 2 — PR #31 de ValeriaMSilva (Modelador de Diagramas de Casos de Uso)

**PR revisada:** `#31 - A2 Modelador de diagramas de casos de uso y docs IA`
**Autora:** ValeriaMSilva
**Rol:** Modelador de Diagramas de Casos de Uso

### Prompt utilizado en Copilot Agent Mode

```
Lee el archivo anexos/introduccion.md de este repositorio como contexto del proyecto.

El sistema es un gestor de turnos para un consultorio médico.
Los actores del sistema son: Paciente, Secretaria y Doctor.
Los 5 casos de uso definidos en introduccion.md son:
1. Solicitar turno — actores: Paciente y Secretaria
2. Cancelar turno — actores: Paciente y Secretaria
3. Registrar llegada del paciente — actores: Paciente, Secretaria y Doctor
4. Registrar al paciente — actores: Paciente y Secretaria
5. Ver agenda — actor: Doctor

Revisá los archivos .puml agregados en esta PR, ubicados en 
diagramas/02-casos-de-uso/.

Validá que cada diagrama PlantUML sea coherente con:
- Los casos de uso y actores documentados en introduccion.md
- Los requisitos funcionales RF1 a RF5 (gestión de turnos, visualizar agenda, 
  notificaciones, gestión de disponibilidad, check de asistencia)

Para cada diagrama verificá:
1. ¿Los actores representados coinciden con los definidos para ese caso de uso?
2. ¿Las relaciones de inclusión y extensión están correctamente modeladas?
3. ¿Los 5 casos de uso de introduccion.md están todos representados?
4. ¿Hay relaciones incorrectas o que no correspondan al sistema?
5. ¿Los archivos .png fueron generados y están en la carpeta correcta?

Indicame los cambios concretos sugeridos con referencia al archivo y línea del .puml.

Publica los comentarios directamente en la Pull Request en las líneas correspondientes

No respondas el chat salvo para el resumen final
```

### Archivos de contexto referenciados

- `anexos/introduccion.md`
- `diagramas/02-casos-de-uso/*.puml` (archivos de la PR)
- `diagramas/02-casos-de-uso/*.png` (imágenes exportadas)

### Output de Copilot (resumen)

Copilot analizó los 5 archivos `.puml` y sus correspondientes `.png` contra los casos de uso, actores y RF1–RF5 de `introduccion.md`. Resultados:

**Cobertura de los 5 casos de uso:** completa — todos tienen `.puml` y `.png`. ✅

**Sintaxis `<<include>>` / `<<extend>>`:** en inglés en todos los archivos. ✅

**Cobertura de requisitos funcionales:**

| RF | Estado |
|---|---|
| RF1 — Gestión de turnos | ✅ Cubierto por CU1 y CU2 |
| RF2 — Visualizar agenda | ✅ Cubierto por CU5 |
| RF3 — Notificación automática (WhatsApp) | ⚠️ Solo modelada en CU2; ausente en CU1 |
| RF4 — Disponibilidad y bloqueo | ⚠️ No modelada en CU5 |
| RF5 — Check de asistencia | ✅ Cubierto por CU3 |

**Problemas detectados:**

1. **`02-caso-uso-cancelar-turno-02.puml` L6** — El actor `Paciente` está declarado pero no tiene asociación con `UC1 "Cancelar turno"`. Según `introduccion.md`, CU2 tiene actores Paciente y Secretaria. Falta `Paciente -- UC1`.
2. **`02-caso-uso-registrar-llegada-03.puml` L4–5** — El actor `Paciente` no está declarado en el diagrama. CU3 requiere actores Paciente, Secretaria y Doctor según `introduccion.md`. El flujo principal comienza con la llegada del paciente.
3. **`02-caso-uso-registrar-llegada-03.puml` L8–10** — `UC4 "Ver lista de espera"` está conectado al `Doctor` pero no tiene ninguna relación con `UC1 "Registrar llegada del paciente"`. El caso de uso queda aislado sin vínculo al flujo central.
4. **`02-caso-uso-registrar-paciente-04.puml` L12** — `UC5 "Solicitar turno"` está declarado sin ninguna relación en el diagrama (usecase fantasma). El comentario en L11 lo asocia incorrectamente a RF5 (Check de asistencia), cuando "Solicitar turno" corresponde a CU1 y RF5 es check de asistencia.
5. **`02-caso-uso-registrar-paciente-04.puml` L20** — El archivo no tiene la directiva de cierre `@enduml`.

### Ajustes realizados al output de la IA

Todos los comentarios generados por Copilot fueron revisados y considerados pertinentes. Se publicaron íntegramente en la PR sin modificaciones.

- ✅ Actor `Paciente` no asociado en CU2 — aceptada, discrepancia directa con los actores definidos en `introduccion.md`.
- ✅ Actor `Paciente` ausente en CU3 — aceptada, CU3 define 3 actores y el flujo comienza con la llegada del paciente.
- ✅ `UC4 "Ver lista de espera"` aislada en CU3 — aceptada, un caso de uso sin relación al flujo central es un error de modelado.
- ✅ UC5 fantasma con RF incorrecto en CU4 — aceptada, el usecase está desconectado y el comentario referencia un RF equivocado.
- ✅ `@enduml` faltante en CU4 — aceptada, el archivo queda sintácticamente incompleto.
- ✅ RF3 sin cobertura en CU1 — aceptada, RF3 es un requisito explícito de la solicitud de turno.
- ✅ RF4 sin cobertura en CU5 — aceptada, RF4 se vincula directamente con la gestión de la agenda del doctor.

### Request Changes cargados en el diff de la PR

| Archivo | Cambio sugerido |
|---|---|
| `diagramas/02-casos-de-uso/02-caso-uso-cancelar-turno-02.puml` L6 | Agregar `Paciente -- UC1` (actor Paciente no está asociado al caso de uso) |
| `diagramas/02-casos-de-uso/02-caso-uso-registrar-llegada-03.puml` L4–5 | Agregar `actor Paciente` y `Paciente -- UC1` (actor ausente; CU3 requiere Paciente, Secretaria y Doctor) |
| `diagramas/02-casos-de-uso/02-caso-uso-registrar-llegada-03.puml` L8–10 | Vincular `UC4 "Ver lista de espera"` al flujo central con `<<extend>>`, o retirarlo a un diagrama propio |
| `diagramas/02-casos-de-uso/02-caso-uso-registrar-paciente-04.puml` L12 | Eliminar `UC5 "Solicitar turno"` (usecase sin relación y comentario con RF incorrecto) |
| `diagramas/02-casos-de-uso/02-caso-uso-registrar-paciente-04.puml` L20 | Agregar `@enduml` como cierre del archivo |
| `diagramas/02-casos-de-uso/02-caso-uso-solicitar-turno-01.puml` | Considerar agregar `<<extend>>` para notificación automática (RF3) |
| `diagramas/02-casos-de-uso/02-caso-uso-ver-agenda-05.puml` | Considerar agregar `<<extend>>` para bloqueo de horarios (RF4) |

**Review publicada:** https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/31#pullrequestreview-4103233925

---

## Code Review 3 — PR #28 de caterinacerdan (Especialista en Escenarios de Casos de Uso)

**PR revisada:** `#28 - Feature/espec escenarios casos uso add escenario 1`
**Autora:** caterinacerdan
**Rol:** Especialista en Escenarios de Casos de Uso

### Prompt utilizado en Copilot Agent Mode

```
Lee el archivo anexos/introduccion.md de este repositorio como contexto del proyecto.

El sistema es un gestor de turnos para un consultorio médico.
Los 5 casos de uso definidos son:
1. Solicitar turno — actores: Paciente y Secretaria
2. Cancelar turno — actores: Paciente y Secretaria
3. Registrar llegada del paciente — actores: Paciente, Secretaria y Doctor
4. Registrar al paciente — actores: Paciente y Secretaria
5. Ver agenda — actor: Doctor

Revisá los archivos .md de escenarios de casos de uso agregados en esta PR, 
ubicados en diagramas/03-escenarios-casos-de-uso/.

Validá que cada escenario sea coherente con:
- El caso de uso correspondiente documentado en introduccion.md
- Los requisitos funcionales RF1 a RF5 y no funcionales RNF1 a RNF5

Para cada escenario verificá que contenga todos los campos requeridos:
ID única, área, actores, descripción, evento activador, tipo de señal,
pasos del flujo principal (mínimo 5 pasos), precondiciones, postcondiciones,
suposiciones, requerimientos, aspectos sobresalientes, prioridad y riesgo.

Indicame:
1. ¿El flujo principal es consistente con el caso de uso correspondiente en introduccion.md?
2. ¿Las precondiciones y postcondiciones son correctas y completas?
3. ¿La prioridad y el riesgo están justificados en relación a los requisitos?
4. ¿Falta algún campo o hay campos incompletos?
5. ¿El naming de los archivos sigue el formato propuesto 
   (03-nombre-caso-de-uso-nombre-escenario-01.md)?

   Publica los comentarios directamente en la Pull Request en las líneas correspondientes

    No respondas el chat salvo para el resumen final
```

### Archivos de contexto referenciados

- `anexos/introduccion.md`
- `diagramas/03-escenarios-casos-de-uso/*.md` (archivos de la PR)

### Output de Copilot (resumen)

Copilot analizó los 5 archivos de escenarios contra los casos de uso, RF1–RF5 y RNF1–RNF5 de `introduccion.md`. Resultados:

**Campos requeridos:** todos presentes en los 5 escenarios. ✅

**Naming de archivos:** los 5 escenarios siguen el formato propuesto. El índice `escenarios_de_casos_de_uso.md` usa guiones bajos en lugar de guiones. ⚠️

**Cobertura de los 5 casos de uso:** completa. ✅

**Problemas detectados:**

1. **`03-solicitar-turno-exitoso-01.md`** — Requerimientos incompletos: faltan RF3 (notificación automática) y RNF1 (evitar superposición). Precondición incompleta: no menciona que debe haber disponibilidad en la agenda.
2. **`03-cancelar-turno-exitoso-02.md`** — Requerimientos incompletos: faltan RF3 (notificación automática) y RNF4 (historial de modificaciones).
3. **`03-registrar-llegada-del-paciente-exitoso-03.md`** — Prioridad subestimada (Media en lugar de Alta, dado que RF5 es requisito funcional central). Precondición circular ("el paciente debe haber llegado" es el evento activador, no una precondición del sistema). Falta RNF4 en requerimientos.
4. **`03-registrar-paciente-exitoso-04.md`** — La verificación de duplicados se menciona en "Información para los pasos" pero no aparece como paso explícito en el flujo principal. RF1 no es el requerimiento más apropiado (registrar paciente es precondición de RF1, no RF1 en sí).
5. **`03-ver-agenda-exitoso-05.md`** — Prioridad subestimada (Media en lugar de Alta, dado que RF2 es un requisito funcional explícito y el doctor depende de la agenda diariamente). Falta RF4 en requerimientos.
6. **`escenarios_de_casos_de_uso.md`** — Nombre con guiones bajos, inconsistente con el resto del repositorio que usa guiones.

### Ajustes realizados al output de la IA

Todos los comentarios generados por Copilot fueron revisados y considerados pertinentes. Se publicaron íntegramente en la PR sin modificaciones.

- ✅ Requerimientos faltantes en CU1 (RF3, RNF1) — aceptada, la postcondición del escenario menciona bloqueo de disponibilidad, que es exactamente RNF1.
- ✅ Requerimientos faltantes en CU2 (RF3, RNF4) — aceptada, la cancelación dispara notificación y debe quedar en historial.
- ✅ Prioridad subestimada en CU3 y CU5 — aceptada, ambos corresponden a requisitos funcionales explícitos del sistema.
- ✅ Precondición circular en CU3 — aceptada, "el paciente debe haber llegado" describe el evento activador, no el estado previo del sistema.
- ✅ Verificación de duplicados fuera del flujo en CU4 — aceptada, si es parte del flujo debe estar en los pasos numerados.
- ✅ Nombre del índice con guiones bajos — aceptada, inconsistencia de naming con el resto del repositorio.

### Request Changes cargados en el diff de la PR

| Archivo | Cambio sugerido |
|---|---|
| `diagramas/03-escenarios-casos-de-uso/03-solicitar-turno-exitoso-01.md` | Agregar RF3 y RNF1 a Reunir Requerimientos; completar precondición con disponibilidad en agenda |
| `diagramas/03-escenarios-casos-de-uso/03-cancelar-turno-exitoso-02.md` | Agregar RF3 y RNF4 a Reunir Requerimientos |
| `diagramas/03-escenarios-casos-de-uso/03-registrar-llegada-del-paciente-exitoso-03.md` | Cambiar Prioridad a Alta, Riesgo a Medio; corregir precondición circular; agregar RNF4 |
| `diagramas/03-escenarios-casos-de-uso/03-registrar-paciente-exitoso-04.md` | Agregar verificación de duplicados como paso explícito en el flujo principal; ajustar referencia de requerimiento |
| `diagramas/03-escenarios-casos-de-uso/03-ver-agenda-exitoso-05.md` | Cambiar Prioridad a Alta; agregar RF4 a Reunir Requerimientos |
| `diagramas/03-escenarios-casos-de-uso/escenarios_de_casos_de_uso.md` | Renombrar a `escenarios-de-casos-de-uso.md` (guiones en lugar de guiones bajos) |

**Review publicada:** https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/28#pullrequestreview-4095861466

---


## Resumen de reviews realizados

| # | PR | Autora | Rol | Estado |
|---|-----|--------|-----|--------|
| 1 | #26 | carolabenvenuto-uces | Diseñador de Tarjetas CRC | 🔄 Request Changes |
| 2 | #31 | ValeriaMSilva | Modelador de Diagramas de Casos de Uso | 🔄 Request Changes |
| 3 | #28 | caterinacerdan | Especialista en Escenarios | 🔄 Request Changes |
| 4 | #[N] | [Nombre] | [Rol] | [✅ Aprobada / 🔄 Request Changes] |