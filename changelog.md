# Changelog

## [Release Primer Parcial] - 2026-04-25
### Added
- [cursor/esp-extension-lsp-add-anexo-lsp-b591] Aplicación del principio de Sustitución de Liskov (LSP) sobre el diseño del Sistema de Turnos Médicos. Se agregaron el anexo técnico, el diagrama de clases en PlantUML/PNG y la auditoría de IA asociada. PR: pendiente - @FacundoGuiraldes (Especialista en LSP)

## [Release Actividad Obligatoria N°2] - 2026-04-16
### Added
- [feature/documentador-coordinador-a2] Documentación y coordinación del repositorio para AO2. PR: [#30](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/30) - @FacundoGuiraldes (Documentador y Coordinador de Repositorio)
- [feature/espec-escenarios-casos-uso-add-escenario-1] Especialista en 5 escenarios de casos de uso. PR: [#28](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/28) - @caterinacerdan (Especialista en Escenarios de Casos de Uso)
- [feature/modelador-diag-casos-uso-crear-diagramas-v2] Modelador de 5 diagramas de casos de uso en PlantUML. PR: [#31](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/31) - @ValeriaMSilva (Modelador de Diagramas de Casos de Uso)
- [feature/diseniador-tarjetas-crc-add-tarjeta-clase-1-v2] Diseño y organización de 8 Tarjetas CRC. PR: [#26](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/26) - @carolabenvenuto-uces (Diseñador de Tarjetas CRC)

### Fixed
- [fix/rc1-documentacion-ia-cu] fix: reemplazo descripcion de PR por documentacion real de IA con prompt y analisis. PR: [#47](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/47) - @ValeriaMSilva (Modelador de Diagramas de Casos de Uso)
- [fix/formato-changelog-pr31] Corrección de salto de línea y reubicación de PR 31 en changelog. PR: [#31](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/31) - @ValeriaMSilva (Modelador de Diagramas de Casos de Uso)
- [fix/changelog-md-a2] Corrección de estructura del changelog según release. PR: [#37](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/37) - @FacundoGuiraldes (Documentador y Coordinador)
- [fix/fix/adición-PR31-changelog.md] Corrección de estructura del changelog PR: [#33](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/33) - @caterinacerdan (Especialista en Escenarios de Casos de Uso)
- [fix/rc2-indice-herramientas] Reestructurar índice de herramientas como categoría. PR: [#36](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/36) - @carolabenvenuto-uces (Diseñador de Tarjetas CRC)
- [fix/escenarios-formato-a2] Corrección de formato de escenarios. PR: [#42](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/42) - @caterinacerdan (Especialista en Escenarios de Casos de Uso)
- [fix/correccion-diagramas-cu] Ajustes técnicos y semánticos en diagramas de Casos de Uso: límites del sistema (rectangle "Sistema de Turnos Médicos"), relaciones obligatorias (extend→include para notificaciones), reintegración del actor Doctor en CU03, y reestructuración de rutas de archivos (.puml y .png a raíz de diagramas/02-casos-de-uso/). Documentación IA ampliada con prompt literal, output detallado por diagrama e iteraciones. PR: [#43](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/43) - @ValeriaMSilva (Modelador de Diagramas de Casos de Uso)
- [fix/rc5-prompt-ia-disenador] Corrección de formato del prompt en la documentación de IA (`ia/a2/disenador-tarjetas-crc.md`): se reemplazaron las comillas simples por bloques de código triple-backtick para asegurar la reproducibilidad según la rúbrica de evaluación. PR: [#39](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/39) - @carolabenvenuto-uces (Diseñador de Tarjetas CRC)
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
- [fix/doc-coord-...]  Correcciones de formato, changelog y estructura.
  PR: [#13](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/13) - @ValeriaMSilva (Documentador y Coordinador)
- [fix/casos-de-uso-flujos] Corrección de flujos de casos de uso en introduccion.md, ampliando a 5 pasos y mejorando la claridad. PR: [#18](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/18) - @caterinacerdan (Modelador de Casos de Uso)
- [fix/boceto-diagrama-png] Corrección del nombre del archivo PNG del boceto del diagrama de clases.
PR: [#17](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/17) - @carolabenvenuto-uces (Diseñador de Clases)
- [fix/templates-pr] Correción de rutas y templates de feature y realease. PR: [#20](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/20) - @caterinacerdan (Modelador de casos de uso)
- [fix] Reubicación de introduccion.md en anexos y eliminación de duplicado.
