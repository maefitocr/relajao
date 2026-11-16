# ARC-001 — Diagrama de arquitectura y responsabilidades · Registro de la tarea

| Campo | Valor |
|---|---|
| Identificador | ARC-001 |
| Versión | 1.0 |
| Estado | **Aprobado** — 16-nov-2026 |
| Objetivo | Representar los límites de RELAJAO, sus responsabilidades funcionales y sus relaciones, según el Discovery MVP v1.0 aprobado |
| Alcance | Esta tarea **no** define la arquitectura técnica (ver [DEC-001](./DEC-001-stack-y-estilo.md) y [ARC-002](./ARC-002-arquitectura-tecnica.md)) |

---

## Documentos

| Archivo | Contenido |
|---|---|
| [`architecture-context.md`](./architecture-context.md) | Diagramas Mermaid con límites, actores y relaciones principales (contexto + vista funcional consolidada) |
| [`responsibilities.md`](./responsibilities.md) | Tabla de responsabilidades, dependencias R1–R12 y referencias al Discovery |

---

## Checklist de criterios de aceptación

| CA | Criterio | Estado | Evidencia |
|---|---|---|---|
| CA-01 | Contexto del sistema | ✅ Verificado | `architecture-context.md` §2: RELAJAO central, usuario único e interacciones |
| CA-02 | Límites del MVP | ✅ Verificado | `architecture-context.md` §2 (exclusiones de frontera); `responsibilities.md` §5 (restantes) |
| CA-03 | Responsabilidades funcionales | ✅ Verificado | `responsibilities.md` §1–2: F01–F07 completas en cinco agrupaciones, sin capacidades nuevas |
| CA-04 | Separación de responsabilidades | ✅ Verificado | `responsibilities.md` §1: responsabilidad principal y columna "qué NO hace" |
| CA-05 | Relaciones entre capacidades | ✅ Verificado | `responsibilities.md` §3: R1–R12 con propósito, sin protocolos técnicos |
| CA-06 | Persistencia de información | ✅ Verificado | `responsibilities.md` §4: necesidad sin motor ni estrategia |
| CA-07 | Trazabilidad del Discovery | ✅ Verificado | `responsibilities.md` §5: mapeo a F01–F07, E01–E12 y S01–S10 |
| CA-08 | Claridad visual | ✅ Verificado | `architecture-context.md` §4: leyenda; nombres del Discovery; vista consolidada |
| CA-09 | Neutralidad tecnológica | ✅ Verificado | Ambos documentos sin menciones a lenguajes, frameworks, patrones o despliegue; lo técnico vive en DEC-001 y ARC-002 |
| CA-10 | Documentación y revisión | ⏳ Parcial | Dudas identificadas (`responsibilities.md` §6), sin contradicciones conocidas; **pendiente commit y PR** |

---

## Definition of Done

| Condición | Estado |
|---|---|
| Los 10 criterios de aceptación verificados | ✅ 16-nov-2026 |
| Ambos documentos versionados en Git | ⏳ En working copy; pendiente commit y PR |
| Sin contradicciones conocidas con el Discovery funcional aprobado | ✅ Verificado (`responsibilities.md` §5) |
| Decisiones abiertas identificadas, sin bloquear el cierre | ✅ `responsibilities.md` §6 (la selección tecnológica quedó resuelta en DEC-001) |
| Revisado y aprobado explícitamente | ✅ 16-nov-2026 |

---

*RELAJAO · ARC-001 v1.0 · Los documentos se generaron a partir del Discovery funcional v1.0 sin introducir decisiones técnicas nuevas.*
