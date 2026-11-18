# Documentación de RELAJAO

Fecha de revisión: **18-nov-2026**. La documentación se mantiene junto al proyecto y se revisa mediante pull requests.

## Insumos de construcción

| Documento | Para qué se usa | Estado del contenido |
|---|---|---|
| [Incrementos e historias](03-planificacion/incrementos-historias.md) | Elegir entrega, historia y criterios de aceptación | Aprobado — 18-nov-2026; 35 historias pendientes de construcción |
| [SPEC técnico](06-construccion/SPEC-TECNICO.md) | Construir módulos, datos, contratos, seguridad, interfaz y pruebas | Documento aprobado — 18-nov-2026; DTP y puntos abiertos no resueltos siguen pendientes |
| [Modelo de dominio v0.1](04-arquitectura/domain-model.md) | Preservar conceptos, relaciones, estados e invariantes | Aprobado — 18-nov-2026 |
| [SPEC funcional](02-requisitos/SPEC.md) | Consultar la visión funcional integrada y sus dependencias | Documento aprobado — 18-nov-2026; contenido consolidado de la línea base |
| [DEC-001](04-arquitectura/DEC-001-stack-y-estilo.md) y [ARC-002](04-arquitectura/ARC-002-arquitectura-tecnica.md) | Respetar estilo, stack, módulos y fronteras | Aprobados — 16-nov-2026 |

Elegir historia → consultar requisitos → consultar sección técnica y decisiones → implementar cuando los puntos que la condicionan estén resueltos → verificar criterios → demostrar y versionar. La autorización de esta sesión cubre documentación, sin iniciar código ni publicación.

La aprobación de la documentación registra el acuerdo sobre su uso como insumo. No convierte las alternativas técnicas propuestas en decisiones aprobadas ni los criterios pendientes en pruebas realizadas. El SPEC técnico declara sus límites en la sección 17.

## Requisitos funcionales

Los criterios originales se conservan en sus documentos; el backlog los distribuye entre historias sin reducirlos.

| Funcionalidad | Versión aprobada | Documento |
|---|---|---|
| F01 · Gestión de tareas | 1.0 | [Tareas](02-requisitos/F01-tareas.md) |
| F02 · Calendario y planificación | 1.0 | [Calendario](02-requisitos/F02-calendario.md) |
| F03 · Áreas de vida y proyectos | 1.1 | [Áreas y proyectos](02-requisitos/F03-areas-proyectos.md) |
| F04 · Dashboard | 1.16 | [Dashboard](02-requisitos/F04-dashboard.md) |
| F05 · Notificaciones y recordatorios | 1.0 | [Avisos internos](02-requisitos/F05-notificaciones.md) |
| F06 · Progreso y motivación | 1.0 | [Progreso](02-requisitos/F06-progreso-motivacion.md) |
| F07 · Configuración y preferencias | 1.0 | [Configuración](02-requisitos/F07-configuracion.md) |

## Arquitectura y dominio

- [ARC-001 · Contexto y contenedores](04-arquitectura/ARC-001-contexto-y-responsabilidades.md): criterios y cierre del entregable.
- [Contexto C4 nivel 1](04-arquitectura/architecture-context.md): usuario, límite e interacciones.
- [Contenedores C4 nivel 2](04-arquitectura/architecture-containers.md): web, API y PostgreSQL, responsabilidades y relaciones.
- [Responsabilidades funcionales](04-arquitectura/responsibilities.md): dependencias R1–R12 y límites por capacidad.
- [Modelo de dominio](04-arquitectura/domain-model.md): conceptos, cardinalidades, ciclo de vida, reglas y PA-01–09.
- [DEC-001 · Estilo y stack](04-arquitectura/DEC-001-stack-y-estilo.md): decisiones vinculantes.
- [ARC-002 · Arquitectura técnica](04-arquitectura/ARC-002-arquitectura-tecnica.md): capas, módulos y operación prevista.
- [SPEC técnico de construcción](06-construccion/SPEC-TECNICO.md): desarrollo técnico y trazabilidad a historias; sección 17 identifica las decisiones pendientes.

## Línea base y versionado

| Insumo | Estado de versionado comprobado localmente |
|---|---|
| [Discovery v1.0](01-discovery/discovery-v1.0.md) | Congelado e integrado en main; estado histórico al cierre del 15-nov-2026 |
| Requisitos, arquitectura, C4 y modelo de dominio | Disponibles en feature, incluidos en el historial hasta `8b65917`; CA-06 de ARC-001 y CA-08 del modelo cumplidos |
| Backlog, SPEC técnico y actualización documental de esta sesión | Cambios locales pendientes de commit |
| Publicación remota e integración posterior en main | No verificadas en esta revisión local |

El [README del proyecto](../README.md) resume el estado vigente. Las referencias históricas del Discovery a fases sin iniciar permanecen intactas; no describen el avance documental posterior. La documentación aprobada no equivale a producto implementado o validado.

## Organización

| Carpeta | Contenido |
|---|---|
| [01-discovery/](01-discovery/) | Línea base congelada |
| [02-requisitos/](02-requisitos/) | SPEC funcional y F01–F07 |
| [03-planificacion/](03-planificacion/) | Un único backlog de incrementos e historias |
| [04-arquitectura/](04-arquitectura/) | Decisiones existentes, modelo de dominio, diagramas y responsabilidades |
| [05-prototipo/](05-prototipo/) | [Prototipo de interfaz](05-prototipo/prototipo.html), propuesta visual |
| [06-construccion/](06-construccion/) | SPEC técnico aprobado y [guía UI](06-construccion/GUIA-CONSTRUCCION-UI.md), propuesta para aprobación |

El SPEC técnico aprobado v0.2 vive únicamente en `06-construccion/SPEC-TECNICO.md`. Historias, arquitectura, prototipo y construcción conservan sus carpetas separadas y se enlazan desde este índice. Las decisiones se registran junto a arquitectura; no se reserva una carpeta de decisiones con una numeración ya ocupada por planificación. El prototipo y la guía UI mantienen su estado de propuesta.

## Reglas de mantenimiento

1. Discovery v1.0 no se reescribe. Una ampliación de alcance o sustitución de arquitectura se identifica y aprueba expresamente.
2. Cada entregable declara versión, fecha y estado; aprobación, implementación, commit y publicación son estados distintos.
3. El backlog es la fuente de orden, historias y aceptación. El SPEC técnico es la fuente de detalle de construcción. Las reglas funcionales originales siguen en F01–F07.
4. Los diagramas se mantienen en Mermaid dentro del documento dueño; los índices enlazan en vez de duplicar especificaciones.
5. Se trabaja en feature y se revisan los cambios mediante PR; main contiene lo oficial y terminado.
6. Antes de cerrar una historia se actualizan sus referencias técnicas, sus decisiones aplicables y su evidencia de aceptación. Los comandos y controles previstos no se declaran implementados hasta existir y ejecutarse.
