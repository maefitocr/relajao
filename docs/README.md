# Documentación de RELAJAO

Índice de la documentación del proyecto. Sigue el modelo **Docs as Code**: cada cambio entra por pull request y las decisiones de alcance quedan registradas de forma explícita.

## Estructura

| Carpeta | Contenido | Estado |
|---|---|---|
| [`01-discovery/`](01-discovery/) | Discovery funcional v1.0 — línea base congelada del MVP | ✅ Disponible |
| `00-proyecto/` | Visión, roadmap y glosario | 🔜 Planificada |
| `02-requisitos/` | Especificación funcional (SPEC), F01–F07 y casos de uso | 🔜 Planificada |
| `03-decisiones/` | Registro de decisiones (decision log, DEC-00X) | 🔜 Planificada |
| `04-planificacion/` | Hitos y backlog | 🔜 Planificada |
| `05-arquitectura/` | SPEC técnico y ADR — **pendiente de autorización** | ⏸️ Sin iniciar |

Las carpetas planificadas se crean cuando existe su primer documento; no se reservan vacías.

## Reglas de la documentación

1. **El Discovery v1.0 está congelado.** Es la línea base funcional aprobada el 15-nov-2026 y no se edita.
2. **Los cambios de alcance se registran como decisiones** (`DEC-00X` en `03-decisiones/`), nunca reescribiendo documentos aprobados.
3. **Cada documento declara su estado** en una cabecera: `Borrador`, `En revisión` o `Aprobado`, con versión y fecha.
4. **Los diagramas funcionales se escriben en Mermaid** dentro del documento que los usa. Las imágenes (mockups, wireframes) van en `assets/`, referenciadas desde su documento dueño.
5. **Una sola fuente por tema:** el detalle de cada funcionalidad vive en su archivo `F0X`; los documentos integradores (SPEC) enlazan, no duplican.

## Documentos

- [Discovery funcional v1.0](01-discovery/discovery-v1.0.md) — problema, usuario objetivo, F01–F07, exclusiones E01–E12, criterios de éxito S01–S10 y acta de cierre.
