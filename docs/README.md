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
| [`05-arquitectura/`](05-arquitectura/) | Contexto y responsabilidades (ARC-001), decisión de estilo y stack (DEC-001) y arquitectura técnica (ARC-002) | ✅ Disponible |

Las carpetas planificadas se crean cuando existe su primer documento; no se reservan vacías.

## Reglas de la documentación

1. **El Discovery v1.0 está congelado.** Es la línea base funcional aprobada el 15-nov-2026 y no se edita.
2. **Los cambios de alcance se registran como decisiones** (`DEC-00X` en `03-decisiones/`), nunca reescribiendo documentos aprobados.
3. **Cada documento declara su estado** en una cabecera: `Borrador`, `En revisión` o `Aprobado`, con versión y fecha.
4. **Los diagramas funcionales se escriben en Mermaid** dentro del documento que los usa. Las imágenes (mockups, wireframes) van en `assets/`, referenciadas desde su documento dueño.
5. **Una sola fuente por tema:** el detalle de cada funcionalidad vive en su archivo `F0X`; los documentos integradores (SPEC) enlazan, no duplican.

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
- Arquitectura:
  [ARC-001 Registro de la tarea](05-arquitectura/ARC-001-contexto-y-responsabilidades.md) ·
  [Contexto de arquitectura](05-arquitectura/architecture-context.md) ·
  [Responsabilidades y dependencias](05-arquitectura/responsibilities.md) ·
  [DEC-001 Estilo y stack](05-arquitectura/DEC-001-stack-y-estilo.md) ·
  [ARC-002 Arquitectura técnica](05-arquitectura/ARC-002-arquitectura-tecnica.md)
