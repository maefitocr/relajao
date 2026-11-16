# F06 — Progreso y motivación

| Campo | Valor |
|---|---|
| Estado | **Aprobado** |
| Versión | 1.0 |
| Aprobación | 15-nov-2026, dentro del [Discovery funcional v1.0](../01-discovery/discovery-v1.0.md) |
| Cambios posteriores | Ninguno |

## 1. Objetivo

Reforzar la constancia con una gamificación mínima — metas diarias, puntos, insignias y rachas — sin presión ni castigos: **nunca hay penalizaciones por días inactivos**.

## 2. Capacidades

| ID | Capacidad | Decisión |
|---|---|---|
| D01 | Resumen de logros (hoy y semana) | Incluir en MVP |
| D02 | Meta diaria opcional (cantidad de tareas) | Incluir en MVP |
| D03 | Progreso hacia la meta | Incluir en MVP |
| D04 | Reconocimiento de logros (mensajes) | **Pospuesto** (ver E12) |
| D05 | Rachas de constancia | Incluir en MVP |
| D06 | Insignias y puntos | Incluir en MVP |
| D07 | Historial semanal (últimos siete días) | Incluir en MVP |
| D08 | Sin penalizaciones | Incluir en MVP |

Valores de gamificación aprobados explícitamente junto con F06: **10 puntos por tarea principal completada**, **tres insignias iniciales** y **rachas basadas en la meta diaria**.

## 3. Reglas de negocio

| Código | Regla |
|---|---|
| RN-F06-01 | Contabilizar tareas principales completadas usando información de F01 |
| RN-F06-02 | Excluir subtareas y tareas canceladas del conteo |
| RN-F06-03 | Contar cada ocurrencia recurrente completada una sola vez |
| RN-F06-04 | Asignar el logro al día local de finalización, según la zona horaria de F02 |
| RN-F06-05 | Meta diaria opcional, en cantidad de tareas |
| RN-F06-06 | Sin meta configurada: mostrar logros sin porcentaje ni rachas nuevas |
| RN-F06-07 | Progreso = completadas del día ÷ meta diaria; indicador limitado visualmente al 100 % |
| RN-F06-08 | Día cumplido cuando las completadas alcanzan o superan la meta |
| RN-F06-09 | Racha = días consecutivos con meta cumplida; un día sin cumplimiento interrumpe la continuidad sin sanciones |
| RN-F06-10 | 10 puntos por tarea principal completada, sin duplicarlos al consultar de nuevo |
| RN-F06-11 | Tres insignias iniciales: primera tarea completada, primera meta diaria alcanzada y racha de 3 días |
| RN-F06-12 | Se conservan puntos e insignias aunque se interrumpa una racha |
| RN-F06-13 | Mostrar los últimos siete días de actividad, incluidos los días con cero tareas |
| RN-F06-14 | Actualizar indicadores cuando cambie una finalización; evitar puntos o logros duplicados |
| RN-F06-15 | Sin penalizaciones, puntuaciones negativas, comparaciones entre usuarios ni notificaciones motivacionales |
| RN-F06-16 | Mostrar los indicadores en una sección compacta del Dashboard (F04), sin duplicar el progreso de proyectos de F03 |

## 4. Criterios de aceptación (17)

| Código | Criterio |
|---|---|
| CA-F06-01 | Al completar una tarea principal aumenta el conteo del día de finalización |
| CA-F06-02 | Las subtareas y tareas canceladas no aumentan los indicadores |
| CA-F06-03 | Cada ocurrencia recurrente completada se cuenta de manera independiente, sin duplicaciones |
| CA-F06-04 | El usuario puede establecer, modificar o desactivar su meta diaria |
| CA-F06-05 | Con meta activa, el progreso refleja la relación entre completadas y objetivo |
| CA-F06-06 | Sin meta, se muestra actividad sin exigir cumplimiento |
| CA-F06-07 | Al alcanzar la meta, el día queda registrado como cumplido |
| CA-F06-08 | La racha aumenta cuando se cumplen metas en días consecutivos |
| CA-F06-09 | Un día sin cumplimiento interrumpe la racha sin restar puntos o insignias |
| CA-F06-10 | Completar una tarea principal otorga los puntos definidos una sola vez |
| CA-F06-11 | Las tres insignias iniciales se desbloquean al cumplir sus condiciones |
| CA-F06-12 | Puntos e insignias permanecen visibles después de interrumpirse una racha |
| CA-F06-13 | El historial muestra las tareas completadas en cada uno de los últimos siete días |
| CA-F06-14 | Los indicadores respetan la fecha local de finalización |
| CA-F06-15 | Cambiar una tarea de completada a otro estado ajusta los conteos y evita recompensas duplicadas |
| CA-F06-16 | F06 se presenta de forma compacta en el Dashboard sin duplicar el progreso de proyectos |
| CA-F06-17 | No aparecen mensajes motivacionales automáticos, penalizaciones ni comparaciones entre usuarios |

## 5. Fuera de alcance

Tienda de recompensas, niveles, rankings y catálogo ampliable de insignias (E08) · mensajes motivacionales automáticos (E12, D04 pospuesta).

## 6. Dependencias

- **F01:** finalizaciones de tareas principales y sus fechas.
- **F02:** zona horaria para asignar el día local del logro.
- **F04:** sección compacta donde se muestran los indicadores.
- **F07:** configuración de la meta diaria.
