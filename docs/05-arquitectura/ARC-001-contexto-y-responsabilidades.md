# ARC-001 — Contexto y contenedores iniciales · Plan 1

| Campo | Valor |
|---|---|
| Identificador | ARC-001 |
| Versión | 1.1 |
| Estado | **Aprobado** — 18-nov-2026; pendiente versionar esta revisión |
| Antecedente | Versión 1.0 registrada como aprobada el 16-nov-2026; revisión 1.1 aprobada explícitamente por el responsable del producto el 18-nov-2026 |
| Objetivo | Visualizar actores, límites y responsabilidades técnicas mediante C4 niveles 1 y 2 |
| Alcance | Documentar Discovery, ARC-002 y DEC-001 sin nuevas decisiones arquitectónicas ni implementación |

## 1. Documentos

- [architecture-context.md](architecture-context.md) §2: contexto C4 nivel 1; persona, sistema e interacciones.
- [architecture-containers.md](architecture-containers.md): contenedores C4 nivel 2; web, API, PostgreSQL, responsabilidades y relaciones.
- [responsibilities.md](responsibilities.md): responsabilidades y dependencias funcionales R1–R12.
- [ARC-002](ARC-002-arquitectura-tecnica.md) y [DEC-001](DEC-001-stack-y-estilo.md): arquitectura y decisiones que sustentan las vistas.

## 2. Criterios de aceptación del Plan 1

Esta matriz adopta los seis criterios del plan del responsable del producto. Sustituye el checklist de diez criterios para evaluar esta revisión, sin cambiar decisiones aprobadas.

| CA | Criterio | Estado | Evidencia |
|---|---|---|---|
| CA-01 | El diagrama de contexto identifica al usuario, RELAJAO y las interacciones externas aplicables al MVP | Aprobado — 18-nov-2026 | Contexto §2: persona y sistema; E01/E04/E09 explican la ausencia de sistemas externos conectados |
| CA-02 | El diagrama de contenedores identifica las unidades ejecutables y almacenes de datos previstos, sin confundir módulos lógicos con contenedores C4 | Aprobado — 18-nov-2026 | Contenedores §1–2: web en navegador, API en servidor y PostgreSQL; diferencia entre C4, Docker y módulos |
| CA-03 | Cada contenedor tiene una responsabilidad clara | Aprobado — 18-nov-2026 | Contenedores §3: responsabilidad y límite de web, API y base de datos |
| CA-04 | Las relaciones y dependencias están documentadas | Aprobado — 18-nov-2026 | Contenedores §2–3: R1–R4 con origen, destino, propósito y tecnología; dependencias internas en responsibilities.md y ARC-002 |
| CA-05 | Los diagramas son consistentes con ARC-002 y DEC-001, o señalan expresamente las decisiones todavía no aprobadas | Aprobado — 18-nov-2026 | Contenedores §4: trazabilidad con arquitectura, F02/F04/F05/F07, S07 y exclusiones; alojamiento concreto pendiente |
| CA-06 | Ambos diagramas están versionados en el repositorio | Pendiente para esta revisión | Las vistas anteriores ya están en feature_initialDocs. La revisión 1.1 y el nuevo documento de contenedores son cambios locales sin commit |

## 3. Coherencia revisada

- Contexto: RELAJAO es un único sistema; la persistencia aparece en nivel 2.
- Contenedores: web, API y PostgreSQL; los siete módulos siguen dentro del monolito. Docker representa empaquetado.
- La API sirve los archivos estáticos y usa una base PostgreSQL gestionada, conforme a ARC-002 §2.
- El Dashboard presenta información y acciones; las reglas permanecen en los módulos responsables.
- Se mantiene la confirmación para sugerencias y la independencia entre planificación y ejecución de tareas.
- Sin integraciones externas, canales externos de notificación, colaboración ni móvil nativo en el MVP.
- Las dudas funcionales del Discovery §10 permanecen abiertas; no se resuelven mediante supuestos en las vistas.

## 4. Condiciones de cierre

| Condición | Estado |
|---|---|
| Diagramas Mermaid y descripciones disponibles localmente | Disponible |
| CA-01 a CA-05 documentados y trazados | Aprobados — 18-nov-2026 |
| Revisión explícita del responsable del producto | Aprobada — 18-nov-2026 |
| Revisión 1.1 y nueva vista versionadas en feature_initialDocs | Pendiente; cambios locales sin commit |
| Publicación o integración en main | Fuera de esta entrega local |

El trabajo se realiza siempre sobre la rama feature; main representa lo oficial y terminado. El responsable del producto aprobó explícitamente los últimos cambios el 18-nov-2026. Esta aprobación cubre el contenido; CA-06 sigue pendiente hasta registrar los cambios en Git. La integración en main no es necesaria para cumplir CA-06: ambos diagramas deben quedar versionados en feature.
