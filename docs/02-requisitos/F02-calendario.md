# F02 — Calendario y planificación

| Campo | Valor |
|---|---|
| Estado | **Aprobado** |
| Versión | 1.0 (basada en la candidata RC2) |
| Aprobación | 14-nov-2026, dentro del [Discovery funcional v1.0](../01-discovery/discovery-v1.0.md) |
| Cambios posteriores | Ninguno |

> **Principio de producto:** *planificar tiempo, no fiscalizar tiempo.* El MVP no registra minutos realmente trabajados, no exige confirmar cada sesión ni mantiene auditoría exhaustiva de actividad.

## 1. Objetivo

Organizar compromisos y reservar tiempo para realizar tareas mediante un calendario diario, semanal y mensual que advierte conflictos y ofrece sugerencias de planificación.

## 2. Modelo conceptual

- **Tareas y subtareas (F01):** estados, prioridades, duración estimada y recurrencias.
- **Bloques:** reservas de tiempo para tareas o subtareas específicas. Un bloque **reserva tiempo; nunca crea otra tarea** y no tiene recurrencia propia.
- **Eventos:** compromisos únicos o recurrentes, independientes de las tareas.
- La planificación y el estado de una tarea son **independientes**: un bloque pasado no demuestra que la tarea se realizó.
- La duración de un bloque sale de su inicio y fin y representa **tiempo reservado**, no trabajado.

## 3. Alcance funcional

| ID | Capacidad | Prioridad |
|---|---|---|
| F02-01 | Vistas diaria, semanal y mensual | P0 |
| F02-02 | Gestión de eventos independientes | P0 |
| F02-03 | Programación de tareas y subtareas mediante bloques | P0 |
| F02-04 | Disponibilidad recurrente y excepciones | P0 |
| F02-05 | Detección de superposiciones | P0 |
| F02-06 | Independencia entre calendario y estados de tareas | P0 |
| F02-07 | Detección de sobrecarga | P1 |
| F02-08 | Sugerencias individuales y reprogramación | P1 |
| F02-09 | Descansos y márgenes configurables | P1 |
| F02-10 | Eventos recurrentes | P1 |
| F02-11 | Horarios habituales sugeridos para tareas recurrentes | P1 |
| F02-12 | Historial mínimo, papelera y restauración de reservas | P1 |

P0 y P1 pertenecen al MVP y se implementan incrementalmente. No se requieren integraciones externas para operar F02.

## 4. Reglas de negocio

| Grupo | Regla |
|---|---|
| Programación | Una tarea o subtarea admite cero, uno o varios bloques |
| Identidad | Cada bloque referencia un elemento de trabajo concreto; nunca crea una tarea nueva |
| Recurrencia | Tareas y eventos pueden repetirse; los bloques no tienen recurrencia propia |
| Sugerencias | El usuario confirma antes de crear, mover o eliminar reservas sugeridas |
| Conflictos | Se advierten superposiciones y sobrecarga, pero se permite guardar manualmente |
| Disponibilidad | Las sugerencias consideran horarios, excepciones, descansos y compromisos fijos |
| Fecha límite | Es independiente del horario reservado y puede vencer sin alterar el estado |
| Historial | Los bloques pasados se conservan sin clasificarlos como realizados o incumplidos |
| Finalización | Completar o cancelar una tarea permite sugerir liberar sus bloques futuros |
| Papelera | Los bloques de tareas eliminadas lógicamente se ocultan y dejan de consumir disponibilidad |
| Restauración | Se recuperan los bloques vinculados, advirtiendo conflictos sin modificar otras reservas |
| Tiempo | Duración estimada opcional; **no se registran minutos reales en el MVP** |

## 5. Criterios de aceptación (27)

### A. Calendario y programación · P0

| ID | Criterio |
|---|---|
| CA01 | El usuario alterna vistas diaria, semanal y mensual y observa los mismos datos en sus fechas correspondientes |
| CA02 | Puede crear, editar y eliminar eventos con inicio y fin válidos, exigiendo que el inicio sea anterior al fin |
| CA03 | Puede asignar varios bloques a una tarea sin crear tareas duplicadas |
| CA04 | Puede programar subtareas individualmente, manteniendo su vinculación con la tarea principal |
| CA05 | Puede configurar y modificar disponibilidad semanal y excepciones para fechas específicas |
| CA06 | Ante una superposición, se muestra una advertencia y se permite confirmar manualmente la reserva |
| CA07 | Crear, mover o eliminar bloques no cambia automáticamente el estado de tareas o subtareas |
| CA08 | F02 funciona sin calendarios externos ni áreas de vida configuradas |

### B. Planificación inteligente · P1

| ID | Criterio |
|---|---|
| CA09 | Detecta planificación superior a la disponibilidad, advierte y permite guardar manualmente |
| CA10 | El usuario configura descansos y márgenes; las sugerencias los respetan sin requerir registro de ejecución |
| CA11 | Una sugerencia individual considera disponibilidad, prioridad, fecha límite y área de vida si existe; funciona sin F03 |
| CA12 | Una redistribución sugerida no modifica reservas hasta que el usuario confirme |
| CA13 | Las sugerencias no mueven compromisos definidos como fijos |

### C. Recurrencia y prevención de duplicados · P1

| ID | Criterio |
|---|---|
| CA14 | El usuario crea eventos recurrentes diarios, semanales y mensuales |
| CA15 | El usuario puede editar una ocurrencia o esta y las futuras, preservando excepciones y eventos pasados. Para eliminar, puede seleccionar únicamente la ocurrencia actual o toda la serie. Eliminar toda la serie retira sus eventos del calendario activo, conservando el historial mínimo de las ocurrencias pasadas |
| CA16 | Un bloque puede vincularse a una ocurrencia recurrente específica sin crear otra tarea |
| CA17 | El horario habitual de una tarea recurrente es opcional; aceptar una sugerencia crea el bloque y rechazarla no cambia nada |
| CA18 | Un doble clic o reintento de confirmación no crea duplicados; el usuario puede crear intencionalmente otra sesión |

### D. Historial, cierre y restauración · P1

| ID | Criterio |
|---|---|
| CA19 | Los bloques pasados permanecen consultables como reservas, sin marcarse como realizados o incumplidos |
| CA20 | Reprogramar una tarea pendiente conserva el bloque pasado y crea una reserva futura sin duplicar la tarea |
| CA21 | Al completar o cancelar una tarea, se sugiere liberar bloques futuros asociados (incluidos los de subtareas); aceptar elimina los seleccionados y rechazar conserva todos |
| CA22 | Los bloques de una tarea eliminada lógicamente se ocultan del calendario activo y no consumen disponibilidad |
| CA23 | Restaurar una tarea recupera sus bloques vinculados y advierte conflictos, sin mover reservas ajenas |

### E. Integridad transversal · P0/P1

| ID | Criterio |
|---|---|
| CA24 | La fecha límite permanece separada de la programación; si vence, se advierte sin cambiar el estado y se permite reprogramar |
| CA25 | Los horarios se crean, guardan y visualizan respetando la zona horaria configurada |
| CA26 | Los bloques no admiten recurrencia propia y la programación de ocurrencias recurrentes no genera tareas duplicadas |
| CA27 | El usuario puede editar o eliminar bloques futuros sin borrar reservas históricas. Eliminar una ocurrencia recurrente no elimina las demás; eliminar toda la serie no borra el historial mínimo de sus ocurrencias pasadas. Ninguna de estas acciones modifica automáticamente los estados de las tareas vinculadas |

> CA15 y CA27 incorporan la resolución de la observación **OBS-F02-01** (eliminación de eventos recurrentes con dos opciones: esta ocurrencia o toda la serie).

## 6. Trazabilidad histórica

Las 43 decisiones (D01–D43) que originaron esta especificación, con su estado (cubierta, ajustada, pospuesta, sustituida o contrato futuro) y su cobertura por criterio, están en la [matriz de trazabilidad del Discovery v1.0](../01-discovery/discovery-v1.0.md#matriz-de-trazabilidad-d01d43). Desglose: 30 cubiertas, 3 ajustadas, 7 pospuestas, 2 sustituidas, 1 contrato futuro.

## 7. Fuera de alcance

Medición de minutos trabajados · cronómetro y cálculo de tiempo restante · recurrencia propia de bloques · planificación automática de varios días · optimización avanzada por patrones · integraciones externas (excluidas del MVP por E01).

## 8. Puntos abiertos

1. **Referencia de D14:** la matriz histórica remite a "F07" como contrato futuro para eventos de calendarios externos, pero F07 quedó como *Configuración y preferencias* y las integraciones están excluidas (E01). En la práctica, los calendarios externos quedan fuera del MVP; la referencia debe corregirse cuando se retome esa capacidad.

## 9. Dependencias

- **F01** aporta tareas, subtareas, estados y recurrencias.
- **F03** aporta el área de vida como insumo opcional de las sugerencias (CA11).
- **F04** consulta eventos, bloques, espacios disponibles y alertas de F02; no implementa un segundo motor de planificación.
- **F07** expone la configuración de disponibilidad y zona horaria definidas aquí.
