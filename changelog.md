# Changelog

## [Release Segundo Parcial] - 2026-06-27

### Added
- [feature/coord-devops-update-docs] Coordinación y documentación del Segundo Parcial. Se creó el índice de patrones de diseño (`anexos/patrones-diseno/patrones_diseno.md`), se actualizó `anexos/anexos.md`, `README.md` y `diagramas/01-diagrama-clases/diagramas_clases.md`, y se documentaron 12 revisiones de PRs asistidas con IA en `ia/segundo-parcial/coordinador-devops.md`. PR: [#137](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/137) | Issue: [#143](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/issues/143) - @FacundoGuiraldes (Coordinador y DevOps)

## [Release Actividad N4] - 2026-06-18

### Added
- [feature/coordinador-devops-add-anexo-cu1] Recuperación de boceto inicial, diseño de diagrama de clases, elaboración de anexo CU1 y actualización de roles en `README.md`. PR: [#105](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/105) - @ValeriaMSilva (Coordinador de Repositorio + Analista Funcional CU1)
- [feature/arquitecto-dominio-add-diagrama-final] Diagrama de clases final unificado, anexo de los cuatro pilares del paradigma orientado a objetos, pseudocódigo del happy path global y documentación de IA. PR: [#109](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/109) | Issues: [#106](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/issues/106), [#107](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/issues/107), [#108](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/issues/108) - @FacundoGuiraldes (Arquitecto de Dominio)
- [feature/analista-cu-2-3-add-anexo-cu2-cu3] Diagramas de clases, anexos funcionales y pseudocódigo orientado a objetos para CU2 (Cancelar Turno) y CU3 (Registrar Llegada del Paciente), con documentación de IA. PR: [#112](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/112) | Issues: [#110](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/issues/110), [#111](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/issues/111) - @carolabenvenuto-uces (Analista Funcional CU2 y CU3)
- [feature/analista-cu-4-5-add-anexo-cu4-cu5] Diseño de diagramas de clases en PlantUML para CU4 y CU5, elaboración de anexo técnico con análisis detallado de clases, atributos, métodos y relaciones UML. PR: [#115](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/115) | Issues: [#113](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/issues/113), [#114](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/issues/114) - @caterinacerdan (Analista Funcional CU4 y CU5)

### Fixed
- [fix/unificar-nombre-obtener-paciente] Unificación `getPaciente()` → `obtenerInfoPaciente()` en diagramas parciales CU2 y CU3 para mantener coherencia con diagrama final y diagramas de secuencia; PR:[#117] - @FacundoGuiraldes (Arquitecto de Dominio)
- [fix/correccion-anexos-md] Limpieza de marcas residuales de conflictos Git y texto duplicado en 04-isp.md resolviendo RCN1 y RCN2; PR:[#129] - @ValeriaMSilva (Coordinadora de Repositorio)
- [fix/correccion-indices-readme] Eliminación de tabla de integrantes en índice de clases y links innecesarios en README para resolver RCN13 y RCN14; PR:[#127] - @ValeriaMSilva (Coordinadora de Repositorio)
- [fix/correccion-actividades-cu1] Resolución de RCN4 conectando el nodo STOP en el diagrama de actividades del CU1; PR:[#126] - @ValeriaMSilva (Coordinador de Repositorio)
- [fix/limpieza-repo] Eliminación de archivo de imagen genérico mal ubicado en el directorio de anexos funcionales; PR:[#123] - @ValeriaMSilva (Coordinadora de Repositorio)
- [fix/correccion-diagrama-cu1] Resolución de RC5, RC6, RC7, RC9 y RC10 en el diagrama de clases del CU1; PR:[#122] - @ValeriaMSilva (Coordinadora de Repositorio / Analista CU1)
- [fix/correccion-rc-anexo-cu1] Resolución de RC1, RC2 y RC4 en Anexo CU1 ajustando trazabilidad, formato de pseudocódigo y enlaces a diagramas; PR:[#120] - @ValeriaMSilva (Coordinadora de Repositorio / Analista CU1)
- [fix/analista-cu2-cu3-correcciones] Resolución de RC13, RC14, RC15, RC16, RC18, RC19, RC20, RC21, RC22, RC23, RC26 y RC27 en diagramas de clases parciales y especificaciones de pseudocódigo en anexos funcionales para CU2 y CU3, eliminando identificadores relacionales y asegurando consistencia estructural OO pura; PR:[#121] - @carolabenvenuto-uces (Analista Funcional CU2 y CU3)
- [fix/correcciones-rc-cu4-cu5] Resolución de RC24, RC25, RC28, RC29, RC31, RC32, RC34 y RC35 en diagramas de clases de CU4 y CU5, eliminando atributos ID, ajustando relaciones estructurales a dependencias/composiciones y corrigiendo índices del análisis funcional; PR:[#119] - @caterinacerdan (Analista Funcional CU4 y CU5)
- [fix/correccion-rcn5-al-rcn10] Resolución de RCN5, RCN7, RCN8, RCN9 y RCN10 en anexos funcionales de CU2 y CU3; cerrando bloques de pseudocódigo, completando tablas de clases involucradas (incluyendo Secretaria, Paciente y Usuario), reparando rutas relativas de diagramas; PR:[#130] - @carolabenvenuto-uces (Analista Funcional CU2 y CU3)
- [fix/rc11-13] Simplificación de índices generales del repositorio y agregado de enlaces cruzados para trazabilidad explícita de artefactos; PR:[#128] - @FacundoGuiraldes (Arquitecto de Dominio)
- [fix/diag-final-cortado] Corrección de inconsistencias en diagrama de clases final: eliminación de relación incorrecta ITurnoService, composición Agenda-Turno y dependencia EstadoTurno; regeneración de PNG sin cortes. PR:[#131] - @FacundoGuiraldes (Arquitecto de Dominio)
- [fix/correccion-enlaces-rotos] Corrección de enlaces en CU1 y refinamiento de pseudocódigo en CU2 y CU3 resolviendo RCN1 a RCN10; PR:[#132] - @ValeriaMSilva (Coordinadora de Repositorio)
- [fix/resolucion-rcn1-rcn4-rcn5-rcn10] Resolución definitiva de RCN1, RCN4, RCN5 y RCN10 en anexos de CU1, CU2 y CU3; reparación de ruta del diagrama de clases de CU1, conexión del flujo de control al nodo STOP terminal en actividades, cierre hermético de bloques Markdown y reescritura de pseudocódigos bajo paradigma OO puro (incorporando SalaEspera y removiendo parámetros de IDs relacionales); PR:[#133] - @carolabenvenuto-uces (Analista Funcional CU2 y CU3)
- [fix/correciones-01-solicitar-turno] Corrección de inconsistencias en el anexo funcional 01-solicitar-turno.md: ajuste de relaciones UML, inclusión del actor Doctor en diagrama de secuencia, unificación de nomenclatura de métodos y actualización de enlaces a tarjetas CRC; PR:[#134] - @caterinacerdan (Analista Funcional CU4 y CU5)

## [Release Actividad N3] - 2026-05-21

### Added
- [feature/doc-coord-repo-update-readme-md] Estructuración inicial de carpetas, diseño de plantillas de IA e integración de enlaces de navegación en `README.md`. PR: [#78](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/78) - @carolabenvenuto-uces (Documentador y Coordinador)
- [feature/esp-secuencia-add-diagrama-secuencia-5] Diseño y mapeo de los Diagramas de Secuencia de los escenarios para los 5 Casos de Uso. PR: [#84](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/84) - @ValeriaMSilva (Especialista en Diagramas de Secuencia)
- [feature/esp-actividades-1-2-add-diagrama-actividad-1] Generación y documentación de los Diagramas de Actividades para los Casos de Uso 1 y 2. PR: [#87](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/87) | Issues: [#85](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/issues/85), [#86](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/issues/86) - @caterinacerdan (Especialista en Diagramas de Actividades - Casos de Uso 1 y 2)
- [feature/esp-actividades-3-4-5-add-diagramas] Desarrollo de los Diagramas de Actividades y reportes de IA para los Casos de Uso 3, 4 y 5. PR: [#88](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/88) | Issues: [#90](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/issues/90), [#91](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/issues/91), [#92](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/issues/92) - @FacundoGuiraldes (Especialista en Diagramas de Actividades - Casos de Uso 3, 4 y 5)
- [feature/doc-coord-repo-update-readme-md] Consolidación final de portadas, unificación de índices planos y registro formal de las 4 auditorías técnicas de IA. PR: [#93](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/93) - @carolabenvenuto-uces (Documentador y Coordinador)

### Fixed
- [fix/correcciones-secuencia] Corrección de formato en mensajes de retorno de Diagramas de Secuencia. PR: [#96](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/96) - @ValeriaMSilva (Especialista en Diagramas de Secuencia)
- [feature/doc-coord-repo-update-readme-md] Actualización integral del `README.md`: se reestructuró la navegación para cumplir con la auditoría de calidad de Copilot, integrando enlaces a todos los índices previos (A2, Parcial) y nuevos (A3). - @carolabenvenuto-uces (Documentador y Coordinador)
- [feature/doc-coord-repo-update-readme-md] Actualización de la tabla de integrantes con los nuevos roles asignados para la Actividad N3. - @carolabenvenuto-uces (Documentador y Coordinador)
- [fix/correccion-indices-readme-coordinador] Corrección de formato del índice de diagramas de actividades, reestructuración del `README.md` para asegurar coherencia conceptual del modelo dinámico y actualización de `diagramas/diagramasUML.md` con la complementariedad de modelos. PR: [#95](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/95) - @carolabenvenuto-uces (Documentador y Coordinador) 
- [fix/correccion-puml-caso-de-uso] correccion de la sintaxis de puml y restauración de actividad 2 caso de uso. PR: [#97](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/97) - @caterinacerdan (Especialista en diagramas de actividades caso de uso 1 y 2)
- [fix/esp-actividades-3-4-5-doc-ia] Corrección de cierres de flujo en diagramas de actividades (un único `stop`; `END` en alternativos) y actualización de documentación IA. PR: [#98](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/98) - @FacundoGuiraldes (Especialista en Diagramas de Actividades)
- [fix/rc-1-18-19-20] Corrección adicional de los Diagramas de Actividades para los Casos de Uso 3, 4 y 5. PR: [#101](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/101) - @FacundoGuiraldes (Especialista en Diagramas de Actividades - Casos de Uso 3, 4 y 5)

## [Release Primer Parcial] - 2026-04-25
### Added
- [feature/especialista-dip-analisis-solid] Análisis técnico del principio DIP, marco teórico y diseño de diagrama UML (puml/png) para desacoplamiento de servicios. PR: [#51](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/51) | Issue: [#50](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/issues/50) - @carolabenvenuto-uces (Especialista en Inversión de Dependencias)
- [feature/esp-srp-add-anexo-srp] Análisis técnico del principio SRP, marco teórico y diseño de diagrama UML (puml/png) para separación de responsabilidades. PR: [#53](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/53) | Issue: [#52](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/issues/52) - @caterinacerdan (Especialista en SRP)
- [feature/esp-isp-add-anexo-isp] Análisis técnico del principio ISP, marco teórico y diseño de diagrama UML (puml/png) para segregación de interfaces. PR: [#55](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/55) | Issue: [#54](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/issues/54) - @ValeriaMSilva (Especialista en ISP)
- [feature/esp-extension-ocp-add-anexo-ocp] Aplicación del principio Abierto/Cerrado (OCP) sobre el diseño del Sistema de Turnos Médicos. Se agregaron el anexo técnico, el diagrama de clases en PlantUML/PNG y la auditoría de IA asociada. PR: [#61](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/61) | Issue: [#57](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/issues/57) - @FacundoGuiraldes (Especialista en OCP)
- [feature/esp-extension-lsp-add-anexo-lsp] Aplicación del principio de Sustitución de Liskov (LSP) sobre el diseño del Sistema de Turnos Médicos. Se agregaron el anexo técnico, el diagrama de clases en PlantUML/PNG y la auditoría de IA asociada. PR: [#62](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/62) | Issue: [#58](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/issues/58) - @FacundoGuiraldes (Especialista en LSP)
- [feature/documentador-coordinador-repo-update-readme.md] Documentación y coordinación del repositorio. PR: [#64](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/64) - @caterinacerdan (Documentador y Coordinador de Repositorio) | Issue: [#63](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/issues/63)

### Fixed
- [fix/eliminar-referencia-isp] Eliminación de referencia inexistente en documento ISP.PR: [#72](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/72) - @ValeriaMSilva (Especialista en Segregación de Interfaces - ISP)
- [fix/correcciones-formato-isp] Corrección de jerarquía de subtítulos en 04-isp.md y eliminación de archivos residuales. PR: [#70](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/70) - @ValeriaMSilva (Especialista en Segregación de Interfaces - ISP)
- [fix/rc8-formato-prompt-isp] fix: cambiar blockquote a bloque de código triple-backtick en prompt de IA (RC 8). PR: [#66](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/66) - @ValeriaMSilva (Especialista en Segregación de Interfaces - ISP)
- [fix/rc10-diagrama-isp] fix: eliminar dependencia de Paciente con IAgendaMedica en diagrama y docs (RC 10). PR: [#69](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/69) - @ValeriaMSilva (Especialista en Segregación de Interfaces - ISP)

## [Release Actividad Obligatoria N°2] - 2026-04-16
### Added
- [feature/documentador-coordinador-a2] Documentación y coordinación del repositorio para AO2. PR: [#30](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/30) - @FacundoGuiraldes (Documentador y Coordinador de Repositorio)
- [feature/espec-escenarios-casos-uso-add-escenario-1] Especialista en 5 escenarios de casos de uso. PR: [#28](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/28) - @caterinacerdan (Especialista en Escenarios de Casos de Uso)
- [feature/modelador-diag-casos-uso-crear-diagramas-v2] Modelador de 5 diagramas de casos de uso en PlantUML. PR: [#31](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/31) - @ValeriaMSilva (Modelador de Diagramas de Casos de Uso)
- [feature/diseniador-tarjetas-crc-add-tarjeta-clase-1-v2] Diseño y organización de 8 Tarjetas CRC. PR: [#26](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/26) - @carolabenvenuto-uces (Diseñador de Tarjetas CRC)

### Fixed
- [fix/rc1-documentacion-ia-cu] fix: reemplazo descripcion de PR por documentacion real de IA con prompt y analisis. PR: [#47](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/47) - @ValeriaMSilva (Modelador de Diagramas de Casos de Uso)
- - [fix/formato-changelog-pr31] Corrección de salto de línea y reubicación de PR 31 en changelog. PR: [#45](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/45) - @ValeriaMSilva (Modelador de Diagramas de Casos de Uso)
- [fix/changelog-md-a2] Corrección de estructura del changelog según release. PR: [#37](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/37) - @FacundoGuiraldes (Documentador y Coordinador)
- [fix/fix/adición-PR31-changelog.md] Corrección de estructura del changelog PR: [#33](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/33) - @caterinacerdan (Especialista en Escenarios de Casos de Uso)
- [fix/rc2-indice-herramientas] Reestructurar índice de herramientas como categoría. PR: [#36](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/36) - @carolabenvenuto-uces (Diseñador de Tarjetas CRC)
- [fix/escenarios-formato-a2] Corrección de formato de escenarios. PR: [#42](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/42) - @caterinacerdan (Especialista en Escenarios de Casos de Uso)
- [fix/correccion-diagramas-cu] Ajustes técnicos y semánticos en diagramas de Casos de Uso: límites del sistema (rectangle "Sistema de Turnos Médicos"), relaciones obligatorias (extend→include para notificaciones), reintegración del actor Doctor en CU03, y reestructuración de rutas de archivos (.puml y .png a raíz de diagramas/02-casos-de-uso/). Documentación IA ampliada con prompt literal, output detallado por diagrama e iteraciones. PR: [#43](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/43) - @ValeriaMSilva (Modelador de Diagramas de Casos de Uso)
- [fix/rc5-prompt-ia-disenador] Corrección de formato del prompt en la documentación de IA (`ia/a2/diseniador-tarjetas-crc.md`): se reemplazaron las comillas simples por bloques de código triple-backtick para asegurar la reproducibilidad según la rúbrica de evaluación. PR: [#39](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/39) - @carolabenvenuto-uces (Diseñador de Tarjetas CRC)
- [fix/ajustes-tarjetas-crc-rc7-rc8] Ajustes técnicos en tarjetas CRC para cumplir con lógica de negocio y principios de DOO: se agregó la responsabilidad activa "Autorizar sobreturno en su agenda" en `herramientas-agile/tarjetas-crc/04-tarjeta-crc-doctor.md` (asegurando que el control de agenda reside exclusivamente en el Doctor), y se creó la entidad completa `herramientas-agile/tarjetas-crc/09-tarjeta-crc-llegadapaciente.md` para el registro de presencia física con validación de turnos y notificación a sala de espera, resolviendo la alerta crítica de flujo incompleto. PR: [#41](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/41) - @carolabenvenuto-uces (Diseñador de Tarjetas CRC)
- [fix/escenarios-indice-formato-links] Corrección de formato de índice de escenarios: se eliminaron los guiones y se ajustaron los enlaces para mejorar la legibilidad y navegación. PR: [#46](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/46) - @caterinacerdan (Especialista en Escenarios de Casos de Uso)
- [fix/rc1-documentacion-ia-cu] fix: reemplazo descripcion de PR por documentacion real de IA con prompt y analisis. PR: [#47](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/47) - @ValeriaMSilva (Modelador de Diagramas de Casos de Uso)
- [fix/reestructuracion-indices] Reestructuración de índice de herramientas y creación de índice de tarjetas CRC. PR: [#48](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/48) - @carolabenvenuto-uces (Diseñador de Tarjetas CRC)


## [Release Actividad Obligatoria N°1] - 2026-03-29
### Added
- [feature/analista-...] Análisis de requerimientos: RFs, RNFs y NotebookLM.
  PR: [#1](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/1) - @FacundoGuiraldes (Analista de Requerimientos)
- [feature/modelador-...] Casos de uso: 5 CUs del dominio del consultorio.
  PR: [#4](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/4) - @caterinacerdan (Modelador de Casos de Uso)
- [feature/diseniador-...] Diagrama de clases inicial en Excalidraw + PNG.
  PR: [#6](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/6) - @carolabenvenuto-uces (Diseñador de Clases Iniciales)
- [feature/doc-coord-...] README, anexos, introduccion.md, templates y coordinación.
  PR: [#7](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/7) - @ValeriaMSilva (Documentador y Coordinador)
- [feature/doc-coord-repo-update-readme-md] Se agregó el archivo feature-template.md en la ruta correcta (.github/PULL_REQUEST_TEMPLATE/).
  PR: [#16](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/16) - @ValeriaMSilva (Documentador y Coordinador de Repositorio)

### Fixed
- [fix/doc-coord-...]  Correcciones de formato, changelog and estructura.
  PR: [#13](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/13) - @ValeriaMSilva (Documentador y Coordinador)
- [fix/casos-de-uso-flujos] Corrección de flujos de casos de uso en introduccion.md, ampliando a 5 pasos y mejorando la claridad. PR: [#18](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/18) - @caterinacerdan (Modelador de Casos de Uso)
- [fix/boceto-diagrama-png] Corrección del nombre del archivo PNG del boceto del diagrama de clases.
PR: [#17](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/17) - @carolabenvenuto-uces (Diseñador de Clases)
- [fix/templates-pr] Correción de rutas y templates de feature y realease. PR: [#20](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/20) - @caterinacerdan (Modelador de casos de uso)
- [fix] Reubicación de introduccion.md en anexos y eliminación de duplicado.
