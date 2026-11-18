# RELAJAO

> Plataforma de productividad personal para organizar tareas, proyectos y tiempo, con planificación inteligente, seguimiento del progreso y enfoque **Keep Simple**.

## Visión

RELAJAO ayuda a centralizar responsabilidades, planificar el tiempo de forma realista y mantener la constancia sin generar sobrecarga. Combina tres elementos:

- **Organización:** tareas, proyectos y áreas de vida en un solo lugar.
- **Planificación:** calendario, bloques de trabajo, disponibilidad y sugerencias ante conflictos.
- **Motivación:** progreso visible, metas, rachas y gamificación ligera.

El sistema recomienda alternativas, pero el usuario conserva el control de sus decisiones.

> **Principio rector:** no se trata de hacer más cosas, sino de organizarse mejor, avanzar en lo que realmente importa y reconocer los logros sin sentirse abrumado.

## Estado del proyecto

| Fase | Estado |
|---|---|
| 1. Discovery funcional | ✅ Completado — [Discovery v1.0](docs/01-discovery/discovery-v1.0.md) (línea base, 15-nov-2026) |
| 2. Arquitectura y diseño técnico | 🔄 En curso — contexto y responsabilidades ([ARC-001](docs/05-arquitectura/ARC-001-contexto-y-responsabilidades.md)), decisión de stack ([DEC-001](docs/05-arquitectura/DEC-001-stack-y-estilo.md)) y arquitectura técnica ([ARC-002](docs/05-arquitectura/ARC-002-arquitectura-tecnica.md)) aprobados el 16-nov-2026; contexto y contenedores C4 (ARC-001 v1.1) aprobados el 18-nov-2026, con cambios locales pendientes de commit |
| 3. Desarrollo del MVP | ⏸️ Sin iniciar |
| 4. Pruebas y validación | ⏸️ Sin iniciar |

**Arquitectura y stack** ([DEC-001](docs/05-arquitectura/DEC-001-stack-y-estilo.md)): monolito modular con Clean Architecture · TypeScript de extremo a extremo · NestJS (Fastify) · React + Vite · PostgreSQL + Prisma · contrato Zod/OpenAPI · monorepo pnpm + Turborepo · Docker + GitHub Actions.

## Alcance del MVP (resumen)

Siete funcionalidades aprobadas: gestión de tareas (F01), calendario y planificación (F02), áreas de vida y proyectos (F03), dashboard (F04), notificaciones internas (F05), progreso y motivación (F06) y configuración (F07). Quedan explícitamente fuera del MVP las integraciones externas, apps móviles nativas, notificaciones externas y la analítica avanzada, entre otras exclusiones (E01–E12).

El detalle completo — decisiones, reglas de negocio, criterios de aceptación, exclusiones y criterios de éxito — está en la [documentación](docs/README.md).

## Documentación

La documentación sigue el modelo **Docs as Code**: vive en [`docs/`](docs/README.md), se versiona con el código y los cambios de alcance se registran como decisiones explícitas, sin reescribir la línea base aprobada.

## Estado documental vigente — 18-nov-2026

- `main` contiene lo oficial y terminado. El trabajo se realiza siempre sobre `feature_initialDocs`, con las versiones más recientes de los entregables pendientes.
- La aprobación del contenido se distingue del versionado: los últimos diagramas C4 están aprobados; su registro en Git (CA-06) permanece pendiente.
- El Discovery conserva el estado histórico al cierre del 15-nov-2026. Sus referencias a arquitectura sin iniciar describen ese momento. El estado actual se consulta aquí y en el [índice documental](docs/README.md).
- El [modelo de dominio inicial v0.1](docs/05-arquitectura/domain-model.md) del Plan 2 está aprobado el 18-nov-2026, pendiente de commit. La implementación continúa sin iniciar.

## Principios de trabajo

- **Keep Simple:** ante la duda, la capacidad avanzada se pospone a una iteración posterior.
- **Línea base congelada:** el Discovery v1.0 no se modifica; los cambios se registran como solicitudes de cambio.
- **Entrega incremental:** primero un producto desplegable pequeño; las mejoras llegan después.

## Licencia

[MIT](LICENSE)
