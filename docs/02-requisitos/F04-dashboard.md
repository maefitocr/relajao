# F04 — Dashboard

| Campo | Valor |
|---|---|
| Estado | **Aprobado** |
| Versión | 1.16 |
| Aprobación | 15-nov-2026, dentro del [Discovery funcional v1.0](../01-discovery/discovery-v1.0.md) |
| Cambios posteriores | Ninguno |

## 1. Objetivo

Dashboard **híbrido** que combina planificación diaria y progreso personal, con prioridad en *lo que debo hacer hoy*.

**Límite funcional:** el Dashboard consulta y presenta información de F02. No implementa un segundo motor de planificación ni calcula proyecciones semanales.

## 2. Componentes

| Componente | Comportamiento (decisiones D01–D25) |
|---|---|
| Tareas de hoy | Tareas con bloque hoy + tareas con fecha límite hoy, sin duplicados (D03). Orden contextual: bloques en curso y próximos (ventana fija de **120 min**, D10), luego bloques posteriores, al final las que vencen hoy sin horario; se muestran prioridad y fecha límite sin alterar F02 (D09) |
| Acciones sobre tareas | Abrir detalle, completar, iniciar o pausar según F01, y pedir sugerencias de reprogramación a F02 (D11) |
| Completadas hoy | Sección secundaria contraíble, separada de las pendientes (D12) |
| Tareas vencidas | Lista accionable con indicador de atraso: máximo inicial de cinco ordenadas por mayor atraso, contador total y "ver todas" (D04, D23) |
| Captura rápida | Solo el **título es obligatorio**; prioridad, fecha límite y área opcionales, sin salir del Dashboard y sin exigir planificación (D13) |
| Agenda del día | Línea de tiempo diaria por horas, diferenciando compromisos fijos y bloques de tareas (D14); muestra eventos, bloques y espacios disponibles según F02, con opción de pedir sugerencias (D15); planificación manual al seleccionar espacios libres, con confirmación (D16) |
| Progreso | Diario y semanal: completadas hoy, completadas esta semana y resumen de avance de proyectos activos (D07) |
| Proyectos | Favoritos anclados en sección propia, visibles aunque no tengan pendientes; los no favoritos aparecen cuando tienen tareas principales elegibles pendientes (D08 + F03 v1.1); el resto sigue accesible en F03 |
| Panel preventivo | Expandible y **simplificado**: reutiliza conflictos, causas y alternativas de F02, sin proyecciones semanales nuevas (D25, que ajusta D05/D17). Alertas con contexto: conflictos, elementos involucrados y opción de pedir alternativas (D19) |
| Estados vacíos | Mensajes sencillos cuando no hay información (D20) |
| Actualización | Al abrir el Dashboard y después de acciones del usuario que afecten tareas, agenda, progreso o alertas (D21) |
| Layout | Distribución fija y adaptable a escritorio, tableta y móvil, sin reorganización de componentes (D22); indicador de carga sencillo (D24) |

**Pospuesto a v2:** análisis avanzado de carga semanal, proyecciones y recomendaciones automáticas (D18).

> El detalle histórico de las 25 decisiones y el contexto del ajuste D25 (simplificación Keep Simple pedida por el responsable del producto) están en el [Discovery v1.0](../01-discovery/discovery-v1.0.md#f04--dashboard--v116).

## 3. Reglas de negocio numeradas

Derivadas de F03 v1.1 (favoritos y orden):

| Código | Regla |
|---|---|
| RN-F04-42 | Mostrar favoritos en una sección de proyectos anclados |
| RN-F04-43 | Mantener visibles los favoritos aunque no tengan tareas pendientes |
| RN-F04-44 | Evitar duplicados entre favoritos y otros proyectos |
| RN-F04-45 | Mostrar la prioridad de cada proyecto |
| RN-F04-46 | Permitir marcar o desmarcar favoritos desde el Dashboard |
| RN-F04-47 | Mostrar favoritos en una sección independiente |
| RN-F04-48 | Aplicar el mismo orden a favoritos y proyectos no anclados |
| RN-F04-49 | Evitar duplicados entre ambas secciones |

> Las reglas RN-F04-01 a RN-F04-41 de la numeración original no se conservaron textualmente; su contenido funcional está cubierto por las decisiones D01–D25 de la sección 2 (ver [notas de reconstrucción](../01-discovery/discovery-v1.0.md#12-notas-de-reconstrucción)).

### Precisiones aprobadas

- **P01 — Conflictos semanales:** el panel puede mostrar conflictos detectados por F02 en la semana actual, pero no calcula porcentajes de ocupación, pronósticos ni recomendaciones nuevas por carga agregada.
- **P02 — Actualización:** la información se refresca tras una operación confirmada; si una operación falla, no se muestra como completada o guardada.

## 4. Criterios de aceptación (22)

| Código | Criterio |
|---|---|
| CA-F04-01 | Al abrir el Dashboard se muestra información actualizada |
| CA-F04-02 | Se visualizan tareas programadas para hoy o con fecha límite hoy, sin duplicados |
| CA-F04-03 | Orden: bloques actuales, próximos, posteriores y vencimiento de hoy sin bloque |
| CA-F04-04 | Las tareas completadas hoy aparecen en una sección secundaria contraída |
| CA-F04-05 | Las vencidas se muestran por separado: máximo inicial de cinco, contador y acceso al listado completo |
| CA-F04-06 | El usuario puede abrir, iniciar, pausar y completar tareas mediante transiciones válidas de F01 |
| CA-F04-07 | La captura rápida permite crear una tarea indicando solo su título |
| CA-F04-08 | La agenda presenta eventos y bloques con horarios y diferenciación visual |
| CA-F04-09 | La agenda muestra espacios disponibles conforme a F02 |
| CA-F04-10 | El usuario puede seleccionar un espacio y planificar manualmente una tarea, con validación y confirmación |
| CA-F04-11 | El usuario puede solicitar sugerencias de planificación y reprogramación a F02 |
| CA-F04-12 | El progreso diario y semanal usa estados y fechas de finalización de F01 |
| CA-F04-13 | El progreso de proyectos respeta las reglas de cálculo de F03 |
| CA-F04-14 | Los proyectos favoritos permanecen visibles aunque no tengan trabajo pendiente |
| CA-F04-15 | Los proyectos no favoritos se muestran cuando tienen tareas principales elegibles pendientes |
| CA-F04-16 | El panel preventivo muestra alertas contextuales obtenidas de F02 |
| CA-F04-17 | El panel permite expandir conflictos, consultar causas y solicitar alternativas |
| CA-F04-18 | No calcula proyecciones semanales ni modifica automáticamente la planificación |
| CA-F04-19 | Se muestran mensajes sencillos cuando no existe información |
| CA-F04-20 | Actualiza los componentes afectados tras acciones confirmadas |
| CA-F04-21 | La distribución se adapta a escritorio, tableta y móvil sin personalización del layout |
| CA-F04-22 | Indicador de carga inicial y opción de reintento cuando falla la consulta |

## 5. Puntos abiertos

1. **Alcance del primer despliegue:** F04 se aprobó completa, pero es amplia. Queda pendiente definir qué componentes salen en la primera entrega y cuáles después (F02 ya prevé entrega incremental P0/P1).

## 6. Dependencias

- **F01:** estados y transiciones de tareas, captura rápida.
- **F02:** agenda, espacios disponibles, sugerencias, conflictos y alertas.
- **F03:** progreso de proyectos, prioridad y favoritos.
- **F06:** sección compacta de progreso y motivación (RN-F06-16).
