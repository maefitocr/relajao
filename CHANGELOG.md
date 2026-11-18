# Changelog

Todos los cambios relevantes de este proyecto se documentan en este archivo.

El formato se basa en [Keep a Changelog](https://keepachangelog.com/es-ES/1.1.0/) y el proyecto seguirá [Versionado Semántico](https://semver.org/lang/es/) cuando exista código.

## [Unreleased]

### Changed

- Rutas documentales ajustadas a 03-planificacion, 04-arquitectura, 05-prototipo y 06-construccion. El SPEC técnico aprobado v0.2 se conserva como única copia en construcción, sustituyendo el borrador v0.1 duplicado; índices y referencias actualizados.

- Aprobación documental del 18-11-2026 registrada en el backlog y el SPEC funcional; historias aún pendientes de construcción y DTP del SPEC técnico pendientes de decisión. README principal e índice reorganizados como entrada a historias, SPEC técnico, dominio y fuentes funcionales.
- SPEC técnico existente revisado como v0.2: preserva el borrador, distingue arquitectura vigente de propuestas, corrige cardinalidades, códigos de error y alcance de pruebas por incremento; agrega comprobaciones previas a contratos y migraciones.

- Revisión documental del 18-11-2026: estados y enlaces cruzados actualizados en los índices, SPEC y arquitectura; aprobación, versionado e integración se distinguen. Discovery y DEC-001 permanecen intactos. Los controles de CI de ARC-002 se describen como previstos, no implementados.

- Aprobados por el responsable del producto el 18-11-2026: ARC-001 v1.1 con los seis criterios del Plan 1, contexto C4 nivel 1 ajustado y nueva vista de contenedores C4 nivel 2; sin nuevas decisiones de arquitectura. Versionado en feature_initialDocs, commit 8b65917 (CA-06 cumplido).

### Added

- `docs/06-construccion/SPEC-TECNICO.md` como insumo de construcción junto con las historias: módulos, datos candidatos, contratos, algoritmos, interfaz, seguridad, pruebas y trazabilidad. Documento aprobado; decisiones propuestas y publicación siguen pendientes según su estado explícito.

- Backlog funcional del MVP (18-11-2026), aprobado documentalmente: ocho incrementos, 35 historias de usuario y criterios de aceptación trazados a F01–F07 y S01–S10. Sustituye los borradores locales de primera entrega y backlog técnico; una sola planificación, sin cambios al alcance aprobado.

- Modelo de dominio inicial v0.1, aprobado explícitamente el 18-11-2026: catálogo de conceptos, diagramas Mermaid con cardinalidades y estados, reglas DM-01–DM-31 trazadas a F01–F07 y análisis pendiente PA-01–PA-09. Sin diseño físico ni implementación; versionado en feature_initialDocs, commit 8b65917 (CA-08 cumplido).

- `docs/04-arquitectura/` con el contexto y las responsabilidades del sistema (ARC-001: `architecture-context.md` y `responsibilities.md`), la decisión de estilo arquitectónico y stack (`DEC-001`) y la arquitectura técnica con capas, módulos y monorepo (`ARC-002`). Aprobados el 16-11-2026.
- `docs/02-requisitos/` con la especificación funcional integradora (`SPEC.md`) y los requisitos por funcionalidad F01–F07, extraídos de la línea base del Discovery v1.0 con cabecera de estado, reglas de negocio, criterios de aceptación y diagramas Mermaid.
- Estructura inicial del repositorio: README, licencia MIT, `.gitignore` y este changelog.
- `docs/` con su índice y reglas de documentación.
- Discovery funcional v1.0 como línea base congelada del MVP (`docs/01-discovery/discovery-v1.0.md`), aprobada y cerrada el 15-11-2026.
