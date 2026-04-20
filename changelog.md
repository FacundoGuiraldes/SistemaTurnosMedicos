# Changelog

## [Unreleased]
### Added
- [feature/documentador-coordinador-a2] Documentacion y coordinacion del repositorio para la AO2: code reviews asistidos con Copilot Agent Mode (PR #26, #31 y #28), documentacion de prompts/ajustes en `ia/a2/documentador-coordinador.md` y actualizacion del README/changelog.
  PR: [#30](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/30) - @FacundoGuiraldes (Documentador y Coordinador de Repositorio)
- [feature/modelador-diag-casos-uso-crear-diagramas-v2] Modelado de 5 diagramas de casos de uso en PlantUML con sus exportaciones PNG e indice de diagramas UML.
PR: [#31](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/31) - @ValeriaMSilva (Modelador de Diagramas de Casos de Uso)
- [feature/espec-escenarios-casos-uso-add-escenario-1] Especialista en 5 escenarios de casos de uso. 
PR: [#28](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/28) - @caterinacerdan (Especialista en Escenarios de Casos de Uso)
- [feature/diseniador-tarjetas-crc...] Diseño y organización de Tarjetas CRC: 
  - Estructura final de **8 clases** detalladas con diseño orientado a objetos.
  - Creación de carpeta `herramientas-agile/tarjetas-crc/` con archivos individuales.
  - Índice general en `herramientas_agile.md` con enlaces funcionales.
  - Documentación detallada del proceso de refinamiento de IA en `ia/a2/`.
  PR: [#26](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/26) - @carolabenvenuto-uces (Diseñador de Tarjetas CRC)

### Modified
- **Refactorización técnica integral:** Se ajustaron las responsabilidades a formato activo y se sincronizaron los atributos (como `departamento` en Secretaria y colecciones en `Sistema`) con el boceto inicial de Excalidraw.
- **Optimización de Arquitectura:** Mejora en el desacoplamiento de la clase Sistema y aplicación de principios **SOLID** (Responsabilidad Única) en la jerarquía de `Usuario`.
- **Cumplimiento de Requisitos:** Inclusión explícita de la lógica para el **RF3 (Notificaciones)** y validación de flujos de llegada en `Sala de Espera`.
- **Consistencia del Modelo:** Definición de la clase `Usuario` como **abstracta** para garantizar la integridad y coherencia del diseño orientado a objetos.

### Fixed
- [fix/rc2-indice-herramientas] Reestructurar índice de herramientas como categoría. PR: [#36](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/pull/36) - @carolabenvenuto-uces (Diseñador de Tarjetas CRC)

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
Commit: [55fc7ce](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/commit/55fc7ce2f6b20820bacb90f7f1f97f91bda00aab) - @caterinacerdan (Modelador de casos de uso)
- [fix] Corrección de estructura del changelog según release.
Commit: [4c2fe83](https://github.com/FacundoGuiraldes/SistemaTurnosMedicos/commit/4c2fe832221b125bccc1b2577b382999d0fe0041) - @caterinacerdan (Modelador de casos de uso)
