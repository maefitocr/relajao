# F05 — Notificaciones y recordatorios

| Campo | Valor |
|---|---|
| Estado | **Aprobado** |
| Versión | 1.0 |
| Aprobación | 15-nov-2026, dentro del [Discovery funcional v1.0](../01-discovery/discovery-v1.0.md) |
| Cambios posteriores | Ninguno |

## 1. Objetivo

Que el usuario identifique tareas próximas a vencer, tareas vencidas y eventos próximos mediante **avisos internos** de la aplicación, sin depender de notificaciones externas. Sencillo, relevante y sin acumulación de avisos innecesarios.

## 2. Decisiones aprobadas (D01–D15)

| ID | Tema | Decisión |
|---|---|---|
| D01 | Canales | Solo avisos internos en la aplicación (sin correo ni push) |
| D02 | Anticipación | Tareas 24 h antes del vencimiento; eventos 30 min antes; las vencidas permanecen activas |
| D03 | Acciones | Abrir tarea/evento y marcar aviso como leído; la condición de vencimiento sigue visible mientras persista |
| D04 | Limpieza | Eliminar automáticamente cuando dejen de ser relevantes (tarea completada/cancelada o condición ya no se cumple; evento finalizado) |
| D05 | Ubicación | Centro de avisos en el encabezado: campana global con contador de no leídos; sin duplicar en el Dashboard |
| D06 | Tareas recurrentes | Avisos independientes por ocurrencia |
| D07 | Eventos recurrentes | Avisos independientes por ocurrencia, 30 min antes, respetando ediciones y eliminaciones individuales |
| D08 | Orden | Vencidas → eventos próximos → tareas próximas a vencer (por fecha/hora dentro de cada grupo) |
| D09 | Cantidad visible | 10 inicialmente y opción "Ver todos" |
| D10 | Lectura automática | Marcar como leído al abrir el elemento desde el aviso |
| D11 | Marcar todos | Acción global "Marcar todos como leídos" sobre todos los avisos activos |
| D12 | Sin fecha límite | No generar avisos, aunque existan bloques planificados |
| D13 | Cambio de fecha límite | Retirar el aviso anterior y generar uno nuevo sin leer cuando corresponda |
| D14 | Transición a vencida | Sustituir el aviso de proximidad por uno nuevo de vencimiento, sin leer |
| D15 | Ausencia de varios días | Mostrar solo avisos vigentes, sin reconstruir avisos históricos |

## 3. Reglas funcionales

- Los avisos se muestran únicamente dentro de la aplicación, cuando el usuario accede.
- Los avisos de tareas requieren fecha límite; los bloques planificados no generan recordatorios.
- Cada ocurrencia recurrente (de tarea o evento) se evalúa de forma independiente, sin duplicados por ocurrencia y condición.
- Marcar un aviso como leído no elimina su condición ni modifica tareas o eventos.
- "Marcar todos como leídos" afecta a todos los avisos activos, no solo a los 10 visibles.
- Los avisos dejan de mostrarse cuando pierden relevancia.

## 4. Criterios de aceptación (18)

| Código | Criterio |
|---|---|
| CA-F05-01 | Los avisos están disponibles dentro de la aplicación sin canales externos |
| CA-F05-02 | Una tarea con fecha límite genera un aviso al entrar en la ventana de 24 h previas |
| CA-F05-03 | Una tarea vencida y no completada ni cancelada mantiene un aviso activo |
| CA-F05-04 | Un evento genera un aviso dentro de los 30 min anteriores a su inicio |
| CA-F05-05 | Las tareas sin fecha límite no generan avisos, tengan o no bloques |
| CA-F05-06 | Las ocurrencias recurrentes de tareas y eventos producen avisos independientes |
| CA-F05-07 | El centro de avisos está disponible desde la cabecera principal |
| CA-F05-08 | La campana muestra el total de avisos activos sin leer |
| CA-F05-09 | Los avisos se ordenan según D08 |
| CA-F05-10 | Se muestran hasta 10 avisos y "Ver todos" muestra el resto |
| CA-F05-11 | Abrir una tarea o evento desde su aviso lo marca como leído |
| CA-F05-12 | El usuario puede marcar individualmente un aviso como leído |
| CA-F05-13 | "Marcar todos como leídos" actualiza todos los avisos activos y el contador |
| CA-F05-14 | Leer un aviso no modifica ni elimina la tarea, evento o condición que lo originó |
| CA-F05-15 | Los avisos irrelevantes se retiran automáticamente |
| CA-F05-16 | Modificar una fecha límite retira el aviso obsoleto y permite generar otro sin leer |
| CA-F05-17 | Al vencer una tarea, el aviso de proximidad se sustituye por uno de vencimiento sin leer |
| CA-F05-18 | Tras varios días sin acceso solo aparecen avisos vigentes, sin duplicados por ocurrencia y condición |

## 5. Fuera de alcance

Notificaciones push, correo y avisos del navegador (E04) · personalización de anticipaciones · posponer avisos · historial de notificaciones · resúmenes de ausencia · recordatorios por bloques de trabajo.

## 6. Puntos abiertos

1. **Interpretación horaria de fechas límite sin hora explícita:** pendiente de precisar en la especificación de diseño detallado.

## 7. Dependencias

- **F01:** fechas límite, estados y recurrencias de tareas.
- **F02:** eventos, sus ocurrencias recurrentes y la zona horaria.
- **F04:** el centro de avisos vive en el encabezado global; el Dashboard no lo duplica.
