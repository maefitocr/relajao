# Responsabilidades y dependencias

| Campo | Valor |
|---|---|
| Tarea | [ARC-001](./ARC-001-contexto-y-responsabilidades.md) |
| Versión | 1.0; referencias y estados actualizados el 18-nov-2026 |
| Estado | **Aprobado** — 16-nov-2026 |
| Contenido | Tabla de responsabilidades, dependencias funcionales y referencias al Discovery |
| Complemento | [`architecture-context.md`](./architecture-context.md) — diagramas de contexto y vista consolidada |
| Fuente | [Discovery funcional v1.0](../01-discovery/discovery-v1.0.md) (línea base cerrada el 15-nov-2026) |
| Neutralidad | **No** define lenguajes, frameworks, patrones arquitectónicos ni mecanismos técnicos |

---

## Índice

1. [Responsabilidades por agrupación](#1-responsabilidades-por-agrupación)
2. [Responsabilidades por funcionalidad](#2-responsabilidades-por-funcionalidad)
3. [Dependencias funcionales (R1–R12)](#3-dependencias-funcionales-r1r12)
4. [Persistencia de información](#4-persistencia-de-información)
5. [Trazabilidad con el Discovery](#5-trazabilidad-con-el-discovery)
6. [Dudas pendientes y observaciones](#6-dudas-pendientes-y-observaciones)

---

## 1. Responsabilidades por agrupación

Las siete funcionalidades aprobadas (F01–F07) se organizan en cinco agrupaciones. Ninguna agrupación añade capacidades que no estén en el Discovery.

| Agrupación | Funcionalidades | Responsabilidad principal | Qué NO hace (evita duplicidades) |
|---|---|---|---|
| **Organización del trabajo** | F01, F03 | Fuente única de **qué** existe por hacer y **cómo se clasifica** | No reserva tiempo ni decide cuándo se hace algo (eso es de Planificación) |
| **Planificación del tiempo** | F02 | Fuente única de **cuándo**: agenda, disponibilidad, conflictos y sugerencias | No cambia estados de tareas: planificar y ejecutar son independientes (F02-CA07) |
| **Visibilidad y motivación** | F04, F06 | **Presentar y reconocer**: el día de un vistazo y los logros alcanzados | El Dashboard no posee motor propio: consulta a F01/F02/F03/F06; F06 sí calcula sus indicadores de motivación (F04-D25, límite funcional) |
| **Avisos internos** | F05 | **Señalar lo relevante en el momento oportuno**, dentro de la aplicación | No usa canales externos (E04) ni acumula avisos obsoletos (F05-D04) |
| **Cuenta y preferencias** | F07 | **Identidad del usuario y preferencias transversales**: perfil, zona horaria, sesión | No duplica motores: la disponibilidad se valida con reglas de F02 y la meta se calcula en F06 (RN-F07-09, RN-F07-11) |

---

## 2. Responsabilidades por funcionalidad

| ID | Funcionalidad | Responsabilidad documentada |
|---|---|---|
| F01 | Gestión de tareas | Capturar, organizar, ejecutar y completar tareas y subtareas: bandeja de entrada, cinco estados, recurrencias, papelera con recuperación |
| F02 | Calendario y planificación | Reservar tiempo mediante bloques y eventos; administrar disponibilidad, excepciones y descansos; advertir superposiciones y sobrecarga; sugerir con confirmación del usuario |
| F03 | Áreas de vida y proyectos | Clasificar el trabajo en la jerarquía Área → Proyecto → Tareas (cinco áreas predefinidas) y derivar progreso y tiempos estimados desde las tareas elegibles |
| F04 | Dashboard | Presentar en un solo lugar lo que se debe hacer hoy: tareas, agenda, vencidas, alertas, captura rápida y resúmenes; solo consulta y presenta |
| F05 | Notificaciones y recordatorios | Generar y administrar avisos internos por vencimientos de tareas y proximidad de eventos, con limpieza automática de lo irrelevante |
| F06 | Progreso y motivación | Reconocer logros: conteos diarios y semanales, meta diaria opcional, rachas, puntos e insignias, sin penalizaciones |
| F07 | Configuración y preferencias | Centralizar perfil, zona horaria, acceso a disponibilidad y meta diaria; administrar la sesión de la cuenta |

---

## 3. Dependencias funcionales (R1–R12)

Cada dependencia describe una interacción funcional con su propósito. **No se impone ningún protocolo ni mecanismo técnico**: su materialización técnica está descrita en [ARC-002](ARC-002-arquitectura-tecnica.md), conforme a [DEC-001](DEC-001-stack-y-estilo.md).

| Ref | Dependencia | Propósito | Referencia en el Discovery |
|---|---|---|---|
| R1 | F03 → F01 | Una tarea puede pertenecer a un proyecto, directamente a un área o quedar sin clasificar; el progreso y los tiempos del proyecto se derivan de sus tareas elegibles | F03 D01–D16, reglas de cálculo |
| R2 | F01 → F02 | Tareas y subtareas se programan mediante bloques; un bloque reserva tiempo y nunca crea otra tarea; la planificación no modifica estados | F02 modelo conceptual, CA03–CA04, CA07 |
| R3 | F01 → F06 | Las finalizaciones de tareas principales alimentan conteos, metas, rachas, puntos e insignias; canceladas y subtareas no cuentan | RN-F06-01 a RN-F06-03 |
| R4 | F01 → F05 | Las fechas límite generan avisos de proximidad (24 h) y de vencimiento; sin fecha límite no hay aviso | F05 D02, D12–D14 |
| R5 | F02 → F05 | Los eventos generan avisos 30 minutos antes de su inicio, de forma independiente por ocurrencia | F05 D02, D07 |
| R6 | F02 → F04 | El Dashboard consulta agenda, espacios disponibles, conflictos y sugerencias de F02; no implementa un segundo motor de planificación | F04 D14–D19, D25 y límite funcional |
| R7 | F01 → F04 | El Dashboard muestra tareas de hoy y vencidas, permite captura rápida y acciones de estado con las transiciones válidas de F01 | F04 D03–D04, D11, D13 |
| R8 | F03 → F04 | El Dashboard muestra el progreso de proyectos según las reglas de F03, con favoritos anclados y orden por prioridad | CA-F04-13 a 15, RN-F04-42 a 49 |
| R9 | F06 → F04 | Los indicadores de motivación se presentan en una sección compacta del Dashboard, sin duplicar el progreso de proyectos | RN-F06-16 |
| R10 | F02 → F06 | La zona horaria administrada por las reglas de F02 determina el día local al que se asigna cada logro | RN-F06-04 |
| R11 | F07 → F02 | Configuración da acceso a zona horaria, horarios habituales, excepciones y descansos; las modificaciones siguen las validaciones de F02 | RN-F07-05 a RN-F07-09 |
| R12 | F07 → F06 | Configuración consulta, modifica o desactiva la meta diaria; el cálculo de progreso y rachas sigue siendo responsabilidad de F06 | RN-F07-10, RN-F07-11 |

**Convención de lectura:** `A → B` significa que la interacción se origina en la información o decisiones administradas por A y se consume o accede desde B, con el propósito exacto descrito en cada fila.

---

## 4. Persistencia de información

El Discovery exige conservar la información entre sesiones (S07; RN-08 de F01; RN-F03-68 de F03; RN-F07-15 de F07). Todas las agrupaciones confían su información a un almacenamiento persistente único representado en los diagramas.

- **Qué se conserva:** tareas, subtareas, recurrencias, estados y fechas de finalización; bloques, eventos y disponibilidad; áreas, proyectos, prioridades y favoritos; avisos vigentes y su estado de lectura; puntos, insignias, rachas e historial de siete días; perfil, zona horaria y preferencias.
- **Qué no se decide aquí:** motor de base de datos, estrategia de almacenamiento, modelo de datos físico ni mecanismo de respaldo. La selección de PostgreSQL y Prisma ya está aprobada en [DEC-001](DEC-001-stack-y-estilo.md) y [ARC-002](ARC-002-arquitectura-tecnica.md); el modelo físico detallado y los respaldos permanecen pendientes de especificación.

---

## 5. Trazabilidad con el Discovery

### Agrupaciones → criterios de éxito y exclusiones

| Agrupación | Funcionalidades | Criterios de éxito que sostiene | Exclusiones que la acotan |
|---|---|---|---|
| Organización del trabajo | F01, F03 | S01 (flujo completo de tareas), S04 (organización personal), S08 (uso cotidiano sencillo) | E03, E10, E11 |
| Planificación del tiempo | F02 | S02 (planificación funcional) | E01, E07 |
| Visibilidad y motivación | F04, F06 | S03 (visibilidad del día), S06 (motivación funcional) | E07, E08, E12 |
| Avisos internos | F05 | S05 (recordatorios internos) | E04, E05 |
| Cuenta y preferencias | F07 | S07 (persistencia y continuidad, junto con el almacenamiento) | E05, E06 |
| Almacenamiento persistente | Transversal | S07 | — |

S09 (validación con usuarios reales) y S10 (criterios de aceptación) son criterios de proceso: aplican al MVP completo, no a una agrupación concreta.

### Consistencia verificada

- Las siete funcionalidades representadas corresponden exactamente a F01–F07 aprobadas; no se inventó ninguna capacidad nueva.
- Los elementos fuera del límite del MVP corresponden a exclusiones aprobadas E01–E12: la descripción que acompaña al contexto enumera las seis exclusiones de frontera sin dibujar relaciones externas inexistentes (E01, E02, E04, E06, E09, E10); las restantes (E03, E05, E07, E08, E11, E12) acotan capacidades internas y figuran en la tabla anterior.
- Las dependencias R1–R12 provienen de decisiones y reglas aprobadas, citadas una a una en la sección 3.
- No se conocen contradicciones con el Discovery funcional aprobado.

---

## 6. Dudas pendientes y observaciones

Decisiones todavía abiertas, identificadas sin bloquear el cierre de este documento:

| # | Duda | Impacto en este documento | Origen |
|---|---|---|---|
| 1 | **Autenticación y seguridad.** F07 presupone una sesión autenticada (gestión de cuenta y cierre de sesión), y DEC-001 ya selecciona Argon2 y sesión con cookie HttpOnly; los detalles de seguridad permanecen pendientes | Mecanismo definido en DEC-001 §2; esta vista funcional permanece neutral | Discovery §10, punto 6 |
| 2 | **Referencia D14/"F07" en F02.** La matriz de F02 cita "F07" como contrato futuro para eventos externos; F07 final es Configuración y las integraciones están excluidas (E01) | Los calendarios externos quedan fuera del MVP; incorporar ese contrato requeriría una solicitud de cambio | Discovery §10, punto 5 |
| 3 | **Alcance del primer despliegue (F04).** F04 se aprobó completo, pero el orden de entrega incremental no está definido | Los diagramas representan el MVP funcional completo (P0 + P1), no un plan de entrega | Discovery §10, punto 4 |
| 4 | **Selección de tecnologías y estilo arquitectónico.** Resuelta: registrada en [DEC-001](./DEC-001-stack-y-estilo.md) y materializada en [ARC-002](./ARC-002-arquitectura-tecnica.md) | Ninguno: este documento es deliberadamente neutral | Resuelta el 16-nov-2026 |
| 5 | Los demás puntos abiertos del Discovery (recurrencias en días 29–31, trazabilidad de subtareas automáticas, interpretación horaria de fechas límite) son de detalle funcional y **no afectan** límites ni responsabilidades | Sin impacto | Discovery §10, puntos 1–3 |

---

*RELAJAO · Complemento funcional de ARC-001 · Generado a partir del Discovery funcional v1.0 sin decisiones técnicas nuevas.*
