# Documentación de RELAJAO

Índice de la documentación del proyecto. Sigue el modelo **Docs as Code**: cada cambio entra por pull request y las decisiones de alcance quedan registradas de forma explícita.

## Estructura

| Carpeta | Contenido | Estado |
|---|---|---|
| [`01-discovery/`](01-discovery/) | Discovery funcional v1.0 — línea base congelada del MVP | ✅ Disponible |
| [`02-requisitos/`](02-requisitos/) | Especificación funcional (SPEC) y requisitos F01–F07 | ✅ Disponible |
| `02-requisitos/casos-de-uso/` | Casos de uso con diagramas | 🔜 Planificada |
| `00-proyecto/` | Visión, roadmap y glosario | 🔜 Planificada |
| `03-decisiones/` | Registro de decisiones transversales (las de arquitectura viven en `05-arquitectura/`) | 🔜 Planificada |
| `04-planificacion/` | Hitos y backlog | 🔜 Planificada |
| [`05-arquitectura/`](05-arquitectura/) | Contexto y contenedores C4 (ARC-001 v1.1), responsabilidades, DEC-001 y ARC-002 | ✅ Disponible |

Las carpetas planificadas se crean cuando existe su primer documento; no se reservan vacías.

## Estado vigente — 18-nov-2026

| Entregable | Estado del contenido | Estado de versionado |
|---|---|---|
| Discovery v1.0 | Cerrado y congelado — 15-nov-2026 | Integrado en main |
| F01–F07 | Aprobados dentro del Discovery; extraídos en archivos propios | Disponibles en feature_initialDocs |
| SPEC | Consolidado desde la línea base; sin nueva aprobación funcional independiente | Disponible en feature; ajuste local de referencias |
| ARC-001 v1.1, contexto y contenedores C4 | Aprobados — 18-nov-2026 | Cambios locales pendientes de commit; CA-06 pendiente |
| Responsabilidades, DEC-001 y ARC-002 | Aprobados — 16-nov-2026 | Disponibles en feature; correcciones documentales locales en responsabilidades y ARC-002 |
| [Modelo de dominio inicial — Plan 2](05-arquitectura/domain-model.md) | v0.1 aprobado — 18-nov-2026 | Documento local; commit pendiente |

El estado del Discovery y sus apéndices se conserva como registro histórico. Para el avance posterior rigen este índice y los documentos de cada entregable. La aprobación de los diagramas no autoriza implementación ni implica publicación.

## Reglas de la documentación

1. **El Discovery v1.0 está congelado.** Es la línea base funcional aprobada el 15-nov-2026 y no se edita.
2. **Los cambios de alcance se registran como decisiones** (`DEC-00X` en `03-decisiones/`), nunca reescribiendo documentos aprobados.
3. **Cada entregable declara su estado**, versión y fecha: `Borrador`, `En revisión` o `Aprobado`. `Cerrado` identifica la línea base congelada y `Consolidado` una extracción sin decisiones nuevas. Aprobación, commit y publicación se registran por separado; los índices muestran el estado vigente.
4. **Los diagramas funcionales se escriben en Mermaid** dentro del documento que los usa. Las imágenes (mockups, wireframes) van en `assets/`, referenciadas desde su documento dueño.
5. **Una sola fuente vigente por tema:** el Discovery conserva la línea base histórica; el detalle de cada funcionalidad vive en su archivo `F0X`; los documentos integradores (SPEC) enlazan, no duplican.

## Documentos

- [Discovery funcional v1.0](01-discovery/discovery-v1.0.md) — problema, usuario objetivo, F01–F07, exclusiones E01–E12, criterios de éxito S01–S10 y acta de cierre.
- [SPEC funcional](02-requisitos/SPEC.md) — modelo conceptual, principios transversales, mapa de funcionalidades y glosario.
- Requisitos por funcionalidad:
  [F01 Tareas](02-requisitos/F01-tareas.md) ·
  [F02 Calendario](02-requisitos/F02-calendario.md) ·
  [F03 Áreas y proyectos](02-requisitos/F03-areas-proyectos.md) ·
  [F04 Dashboard](02-requisitos/F04-dashboard.md) ·
  [F05 Notificaciones](02-requisitos/F05-notificaciones.md) ·
  [F06 Progreso y motivación](02-requisitos/F06-progreso-motivacion.md) ·
  [F07 Configuración](02-requisitos/F07-configuracion.md)
- [Modelo de dominio inicial v0.1](05-arquitectura/domain-model.md) — conceptos, cardinalidades, estados, catálogo de reglas y puntos abiertos; aprobado el 18-nov-2026, pendiente commit.
- Arquitectura:
  [ARC-001 Registro de la tarea](05-arquitectura/ARC-001-contexto-y-responsabilidades.md) ·
  [Contexto de arquitectura](05-arquitectura/architecture-context.md) · [Contenedores C4 (aprobado)](05-arquitectura/architecture-containers.md) ·
  [Responsabilidades y dependencias](05-arquitectura/responsibilities.md) ·
  [DEC-001 Estilo y stack](05-arquitectura/DEC-001-stack-y-estilo.md) ·
  [ARC-002 Arquitectura técnica](05-arquitectura/ARC-002-arquitectura-tecnica.md)
