# F03 — Áreas de vida y proyectos

| Campo | Valor |
|---|---|
| Estado | **Aprobado** |
| Versión | 1.1 (v1.0 + solicitudes de cambio CR-F03-01 y CR-F03-02) |
| Aprobación | v1.0 y v1.1: 14/15-nov-2026, dentro del [Discovery funcional v1.0](../01-discovery/discovery-v1.0.md) |
| Cambios posteriores | Ninguno |

## 1. Objetivo

Organizar las tareas en una jerarquía simple — **Área → Proyecto → Tareas** — que relacione las actividades con responsabilidades y objetivos, con progreso y tiempos estimados calculados automáticamente.

## 2. Modelo

- **Cinco áreas predefinidas:** Trabajo, Salud, Finanzas, Desarrollo personal y Vida personal. Se puede cambiar su nombre y color; **no** se pueden crear, archivar ni eliminar (decisión Keep Simple; se revisará más adelante).
- **Proyecto:** nombre obligatorio, descripción opcional, área obligatoria. Identidad estable aunque cambie de nombre o área.
- **Tareas:** pueden pertenecer a un proyecto, directamente a un área, o quedar sin clasificación. Movimiento libre entre esos tres destinos conservando estados, subtareas, fechas, recurrencias y reservas.
- **Herencia:** las tareas de un proyecto heredan su área; cambiar el área del proyecto actualiza la clasificación de sus tareas sin modificar estados ni bloques.
- **Navegación:** lista jerárquica de áreas, proyectos y tareas con filtros por área y proyecto, sin dashboards adicionales.
- Al **eliminar un proyecto**, sus tareas quedan asociadas directamente al área anterior.

## 3. Prioridad y favoritos (v1.1)

- Cada proyecto tiene **prioridad** editable: Alta, Media o Baja (inicial: **Media**).
- Cada proyecto puede marcarse como **favorito** (inicial: no). Prioridad y favorito son independientes.
- Orden: favoritos en sección separada; dentro de cada sección, por prioridad descendente (Alta → Media → Baja) y alfabético en caso de empate. Un favorito aparece una sola vez.
- Modificar prioridad o favorito no cambia estados, prioridades ni fechas de sus tareas, y persiste entre sesiones.
- La prioridad del proyecto **no** modifica la prioridad de sus tareas ni reordena bloques en F02.

## 4. Reglas de cálculo

- **Tarea elegible:** tarea principal que no es recurrente, no está cancelada y no está eliminada lógicamente. Las subtareas nunca cuentan por separado.
- **Progreso** = tareas principales completadas ÷ tareas principales elegibles × 100. Sin tareas elegibles: 0 %, sin considerarse completado.
- **Tiempo total** = suma de estimaciones de tareas elegibles, en cualquier estado de ejecución.
- **Tiempo pendiente** = suma de estimaciones de tareas elegibles en estado pendiente, en progreso o pausada. *No representa horas restantes reales:* una tarea de 6 h en progreso conserva sus 6 h hasta completarse.
- Las tareas sin estimación aportan 0 h al agregado.

**Ejemplo.** Proyecto con tareas de 4 h (completada), 6 h (en progreso), 8 h (pendiente), 1 h recurrente (excluida) y 2 h cancelada (excluida) → progreso 33,3 %, tiempo total 18 h, pendiente 14 h.

### Precisiones aprobadas con v1.0

- **P01 — Tareas eliminadas lógicamente:** dejan de participar en progreso y tiempos; al restaurarse vuelven a participar según su estado y clasificación. Eliminar no es lo mismo que cancelar.
- **P02 — Tareas recurrentes en proyectos:** pueden asociarse a un proyecto y se muestran identificadas como recurrentes; ni la serie ni sus ocurrencias contribuyen al progreso o al resumen de tiempo; sus reservas siguen gestionándose en F02.

## 5. Reglas de negocio numeradas

| Código | Regla |
|---|---|
| RN-F03-58 | Las tareas eliminadas lógicamente se excluyen de los indicadores activos |
| RN-F03-59 | Restaurar una tarea recalcula los indicadores correspondientes |
| RN-F03-60 | Las tareas recurrentes permanecen visibles dentro de sus proyectos |
| RN-F03-61 | Las ocurrencias recurrentes conservan su independencia según F01 |
| RN-F03-62 | Las reservas asociadas siguen gestionándose exclusivamente mediante F02 |
| RN-F03-63 | Los proyectos conservan una identidad estable aunque cambien de nombre o área |
| RN-F03-64 | Cada proyecto tiene una prioridad editable (Alta, Media o Baja; valor inicial Media) |
| RN-F03-65 | Cada proyecto puede marcarse o desmarcarse como favorito (valor inicial: no) |
| RN-F03-66 | Prioridad y favorito son propiedades independientes |
| RN-F03-67 | Modificarlas no cambia estados, prioridades ni fechas de sus tareas |
| RN-F03-68 | Los cambios se conservan entre sesiones |
| RN-F03-69 | Ordenar proyectos por prioridad descendente (Alta → Media → Baja) |
| RN-F03-70 | Empates resueltos alfabéticamente por nombre |

> Las reglas RN-F03-01 a RN-F03-57 de la numeración original no se conservaron textualmente; su contenido funcional está cubierto por las decisiones D01–D16 y las secciones 2–4 de este documento (ver [notas de reconstrucción del Discovery](../01-discovery/discovery-v1.0.md#12-notas-de-reconstrucción)).

## 6. Criterios de aceptación (26)

### v1.0 — Áreas y clasificación

| # | Criterio |
|---|---|
| 1 | Existen cinco áreas iniciales con nombre y color editables |
| 2 | No se permite crear, archivar ni eliminar áreas |
| 3 | Una tarea puede tener proyecto, área directa o ninguna clasificación |
| 4 | Las tareas de un proyecto heredan su área |

### v1.0 — Proyectos y movimientos

| # | Criterio |
|---|---|
| 5 | Se pueden crear proyectos con nombre y área obligatorios |
| 6 | Se pueden editar nombre, descripción y área |
| 7 | Eliminar un proyecto conserva sus tareas asociadas directamente al área anterior |
| 8 | Las tareas pueden moverse entre proyectos o quedar fuera de ellos |
| 9 | Los movimientos preservan estados, subtareas, fechas, recurrencias y bloques |
| 10 | Cambiar el área de un proyecto actualiza la clasificación de sus tareas |

### v1.0 — Indicadores

| # | Criterio |
|---|---|
| 11 | El progreso se calcula con tareas principales elegibles |
| 12 | Las subtareas no cuentan individualmente |
| 13 | Las tareas recurrentes, canceladas y eliminadas lógicamente no cuentan |
| 14 | Un proyecto sin tareas elegibles muestra 0 % |
| 15 | Se muestran tiempo total y pendiente estimados |
| 16 | Las tareas sin estimación aportan 0 h |
| 17 | Completar, cancelar, restaurar o mover tareas recalcula los indicadores |

### v1.0 — Experiencia y persistencia

| # | Criterio |
|---|---|
| 18 | La lista jerárquica permite navegar y filtrar por área o proyecto |
| 19 | Las tareas recurrentes siguen visibles y sus ocurrencias conservan las reglas de F01 |
| 20 | Los cambios persisten y no alteran las reglas aprobadas de F01 y F02 |

### v1.1 — Prioridad y favoritos

| Código | Criterio |
|---|---|
| CA-F03-21 | Al crear un proyecto, su prioridad inicial es Media y no es favorito |
| CA-F03-22 | Se puede modificar la prioridad sin afectar las tareas |
| CA-F03-23 | Se puede marcar o desmarcar un proyecto como favorito |
| CA-F03-24 | Los proyectos se ordenan por prioridad descendente y alfabéticamente en caso de empate |
| CA-F03-25 | Prioridad y favorito persisten entre sesiones |
| CA-F03-26 | Cambiar prioridad o favorito no altera progreso, fechas ni bloques de calendario |

## 7. Fuera de alcance

Crear, eliminar o archivar áreas · archivar proyectos · estados manuales de proyecto · proyectos diarios/semanales/mensuales · fechas de inicio o fin de proyecto · cronómetros y horas reales · gráficos avanzados · dependencias entre proyectos o tareas.

## 8. Dependencias

- **F01** define las tareas, sus estados y recurrencias que alimentan los cálculos.
- **F02** gestiona las reservas de las tareas del proyecto; F03 nunca las modifica.
- **F04** muestra los proyectos favoritos (anclados) y los que tienen trabajo pendiente, conforme a RN-F04-42 a RN-F04-49.
