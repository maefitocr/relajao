# RELAJAO — Guía de construcción del UI

Versión 0.1 · Deriva del [SPEC técnico aprobado](SPEC-TECNICO.md#13-frontend-web) y se contrasta con el [prototipo de interfaz](../05-prototipo/prototipo.html).
Estado: propuesta para aprobación. Las decisiones abiertas están en §13 de esta guía.

---

## 1. Principios

1. **Planificar, no fiscalizar.** El sistema advierte, nunca bloquea (superposición, sobrecarga). Toda advertencia permite "Guardar de todos modos".
2. **Keep Simple.** Una acción principal por pantalla. Sin gamificación agresiva: puntos, racha e insignias son informativos.
3. **El usuario decide.** Las sugerencias son efímeras y requieren confirmación explícita.
4. **Estado servidor ≠ estado UI.** Todo dato de dominio vive en TanStack Query; el estado local solo guarda vista, filtros y modales.
5. **Sin actualizaciones optimistas** en operaciones de dominio (transiciones, bloques, confirmaciones). Se muestra pendiente y se invalida al responder.
6. **Accesible por defecto** (WCAG 2.1 AA): foco visible, teclado completo, contraste ≥ 4.5:1, no depender solo del color.

## 2. Tokens de diseño (paleta de marca v1.0, propuesta)

Concepto: productividad sin estrés. Verde Relajao domina; Menta para elementos secundarios; Sol Calmado solo para destacar logros; los colores funcionales se reservan para estados reales.

| Token | Valor | Uso |
|---|---|---|
| `--primary` | #0F766E | acción principal, navegación activa, progreso |
| `--secondary` | #4FD1A5 | acentos suaves, foco de teclado, huecos libres |
| `--accent` | #FBBF24 | logros (meta, insignias), acción "destacada" |
| `--coral` | #FB8B72 | cercanía/energía: contadores, sobrecarga |
| `--warm-bg` | #FFF7ED | paneles de bienvenida y tarjetas cálidas |
| `--info` / `--success` / `--warning` / `--error` | #60A5FA / #22C55E / #F59E0B / #EF4444 | estados reales |
| `--focus` | #8B5CF6 | sesión de enfoque en curso |
| `--text` / `--muted` | #111827 / #6B7280 | texto principal / secundario |
| `--border` / `--bg` / `--surface` | #E5E7EB / #F3F4F6 / #FFFFFF | bordes, fondo, tarjetas |
| `--gradient-brand` | #0F766E → #4FD1A5 | barras de progreso y detalles de marca |
| Modo oscuro (referencia) | fondo #0B1F1E · superficie #134E4A · acento #1F6F64 | fuera del alcance inicial |

**Contraste (WCAG AA).** Los colores funcionales puros no son aptos para texto sobre fondo claro. Regla: sobre un tinte claro se usa la variante oscura del mismo tono (ej. prioridad Alta: texto #B91C1C sobre #FEE2E2; advertencia: #92400E sobre #FEF3C7; éxito: #15803D sobre #DCFCE7). Texto sobre Menta o Sol Calmado va en oscuro (#111827 / #422006), nunca en blanco. Blanco sobre #0F766E cumple AA. Validar cada par antes de aprobar la paleta.

Radios: 16 px tarjetas, 10–12 px controles. Tipografía system-ui 14.5/1.5. Espaciado en múltiplos de 4. Colores de áreas: configurables por el usuario (D04); el prototipo usa tonos apagados por defecto.

## 3. Layout y navegación

- **Header global fijo:** logo · navegación (Hoy, Tareas, Calendario, Proyectos, Configuración) · captura rápida · campana de avisos.
- **Responsive (SPEC §13):** ≥1024 px dos columnas en Dashboard; 640–1023 una columna; <640 navegación inferior fija y captura reducida.
- **Rutas:** `/entrar`, `/`, `/tareas`, `/calendario/:vista` (dia|semana|mes), `/proyectos`, `/configuracion`.
- **Modales:** detalle de tarea, reservar bloque, evento, confirmaciones. Cierran con Esc y clic fuera; devuelven el foco al disparador.

## 3.1 Principios de UX aplicados en el prototipo

| Patrón | Qué hace | Regla que respeta |
|---|---|---|
| **Siguiente paso** | Tarjeta destacada con la tarea en curso o la primera de hoy; acciones Empezar, Completar, Ver detalle | El usuario decide; el sistema propone un único foco |
| **Enfoque** | Botón ▶ inicia la tarea (En progreso) y muestra un cronómetro flotante con Pausar/Completar | Usa solo transiciones válidas del SPEC |
| **Deshacer** | Completar y enviar a papelera ofrecen "Deshacer" 5 s | Reversibilidad; coherente con la tabla de transiciones |
| **Celebración sutil** | Confeti breve al completar; respeta `prefers-reduced-motion` | Refuerzo positivo sin presión |
| **Carga de la semana** | Siete días con barra de carga; coral si hay sobrecarga | Advertir, no bloquear |
| **Mi día** | Barra horizontal 7–21 h con eventos, bloques y hora actual | Visión rápida del tiempo reservado |
| **Tareas agrupadas** | Vencidas · Hoy · Próximos 7 días · Más adelante · Sin fecha | Foco en lo que requiere atención |
| **Lista y tablero** | Alterna entre lista agrupada y columnas por estado; mover con botones | Mismas transiciones del dominio |
| **Búsqueda y filtros** | Texto, prioridad y área; contadores por pestaña | |
| **Atajos** | `N` captura, `/` busca, `Esc` cierra | Accesibilidad por teclado |
| **Estados vacíos** | Icono, título y siguiente acción en cada sección | Nunca una pantalla "muerta" |

Nota: el cronómetro de enfoque, el confeti y el tablero son propuestas de UX del prototipo; no están en el SPEC y requieren aprobación antes de entrar al alcance.

## 4. Catálogo de componentes

| Componente | Props clave | Notas |
|---|---|---|
| `AppHeader` | usuario, avisosNoLeidos | contiene `QuickCapture` y `BellPopover` |
| `QuickCapture` | onSubmit(titulo) | Enter crea tarea en bandeja; título vacío → error inline |
| `BellPopover` | avisos[] | máx. 10 visibles + "Ver todos"; orden vencidas → eventos → tareas |
| `TaskRow` | tarea, acciones | check de completar, chips (prioridad, estimación, límite, área, pasos) |
| `TaskDetail` (modal) | tareaId | edición, transiciones permitidas, subtareas, bloques, sugerencias |
| `StateButtons` | estado | habilita solo transiciones de la tabla del SPEC |
| `SubtaskList` | subs | un nivel, máx. 50; auto-completadas marcadas "automática" |
| `Timeline` | fecha | eje 7–21 h, franja de disponibilidad, eventos 📌, bloques ⏱, huecos libres clicables |
| `CalendarDay/Week/Month` | fecha | mes navega al día al hacer clic |
| `BlockForm` / `EventForm` | valores | flujo de advertencia en dos pasos (§7) |
| `SuggestionList` | propuestas | efímeras; "Aceptar" crea bloque |
| `ProjectCard` | proyecto, progreso | barra, total/pendiente min, favorito, prioridad |
| `ProgressCard` | meta, racha, puntos | sin meta: solo conteo, sin % ni racha |
| `Badges` | insignias | 3 insignias; estado obtenida/pendiente con texto |
| `PreventivePanel` | conflictos[] | solo hechos actuales, sin proyecciones |
| `EmptyState`, `Toast`, `ConfirmDialog` | | ver §8 |

## 5. Pantallas

### 5.1 Dashboard "Hoy" (`/`)
Secciones y precedencia (DTP-21):
1. **Tareas de hoy**, agrupadas: *En curso / próximo (ventana 120 min)* → *Más tarde hoy* → *Vencen hoy sin bloque*. Una tarea con bloque hoy no se duplica en otra sección.
2. **Vencidas** (máx. 5, "Ver todas" lleva a Tareas › Vencidas); excluye las que ya aparecen con bloque hoy.
3. **Completadas hoy** (colapsable).
4. **Agenda de hoy** (timeline).
5. **Progreso**: meta, semana, racha, puntos, historial 7 días, insignias.
6. **Panel preventivo** de la semana: superposiciones y sobrecarga.
7. **Proyectos favoritos** y activos.
Criterios: HU de F04 y F06; DTP-02, DTP-21.

### 5.2 Tareas (`/tareas`)
Pestañas: Bandeja · Activas · Vencidas · Hechas · Canceladas · Papelera.
- Bandeja = tareas activas sin bloque vigente (vista, no estado; DTP-09).
- Papelera: solo "Restaurar"; si sus bloques generan conflicto se avisa.
- Detalle en modal; completar con bloques futuros ofrece "¿Liberar bloques futuros?".

### 5.3 Calendario (`/calendario/:vista`)
Día / Semana / Mes, navegación ◀ ▶ y "Hoy". Acciones: + Evento, + Bloque. Día muestra aviso de sobrecarga. Los bloques pasados son inmutables (sin eliminar).

### 5.4 Proyectos (`/proyectos`)
Cinco áreas predefinidas (solo renombrar/color). Proyectos por área ordenados por prioridad y nombre; tareas directas del área. Eliminar proyecto deja las tareas en el área.

### 5.5 Configuración (`/configuracion`)
Perfil (nombre, zona horaria), disponibilidad, descanso, margen, sesión, meta diaria (vacío = desactivada). Sin apariencia, avisos, exportación ni restablecimiento (E05/E06).

### 5.6 Entrar (`/entrar`)
Formulario correo + contraseña (Argon2 en servidor, cookie HttpOnly). Errores genéricos; sin revelar si el correo existe.

## 6. Mapa de reglas de dominio → comportamiento UI

| Regla | Comportamiento |
|---|---|
| Tabla de transiciones | `StateButtons` deshabilita lo no permitido; el servidor valida de todos modos |
| Completar tarea | subtareas pendientes se marcan automáticas; suma 10 pts una sola vez |
| Fecha límite sin hora (DTP-02) | se interpreta fin del día local |
| Aviso tarea | 24 h antes del límite; aviso evento: 30 min antes |
| Superposición / sobrecarga | advertencia + confirmación; nunca bloquea |
| Bloque | reserva tiempo, nunca crea tareas; no se crea en el pasado |
| Sugerencia | efímera; confirmar con `Idempotency-Key` |
| Meta desactivada | sin porcentaje ni racha |

## 7. Flujo de advertencia en dos pasos

1. Usuario pulsa **Guardar**. Si hay superposición o sobrecarga, no se guarda: se muestra el bloque `warn` con la lista de causas y el botón cambia a **Guardar de todos modos**.
2. Segundo clic confirma y guarda. Cambiar fechas reinicia el flujo.
Se aplica a Bloque y Evento.

## 8. Estados de interfaz

| Estado | Patrón |
|---|---|
| Cargando | esqueleto de tarjeta; nunca bloquear toda la pantalla |
| Vacío | texto breve + acción sugerida (ej. "Nada pendiente para hoy…") |
| Error de red | mensaje inline con "Reintentar" |
| Error de validación | mensaje junto al campo (código del Apéndice B del SPEC) |
| Éxito | toast de 2.5 s, `role="status"` |
| Conflicto de concurrencia | recargar y avisar |

## 9. Accesibilidad

- Todo control accesible por teclado; orden de foco lógico; foco visible 3 px.
- Modales con `role="dialog"`, `aria-modal`, foco atrapado y retorno de foco.
- Botones de icono con `aria-label` (campana, completar, favorito).
- Estado (vencida, prioridad, meta cumplida) siempre con texto además de color.
- Toasts y contadores de avisos anunciados con `aria-live="polite"`.
- Timeline: huecos libres son `role="button"` con `tabindex="0"` y activación por Enter/Espacio.

## 10. Datos: hooks y matriz de invalidación

Convención de claves: `['tareas', filtros]`, `['tarea', id]`, `['calendario', vista, fecha]`, `['proyectos']`, `['dashboard']`, `['avisos']`, `['progreso']`, `['config']`.

| Operación | Invalida |
|---|---|
| Crear/editar tarea | tareas, tarea, dashboard, proyectos, avisos |
| Cambiar estado | tareas, tarea, dashboard, progreso, proyectos, avisos, calendario |
| Subtareas | tarea, tareas, dashboard |
| Crear/eliminar bloque | calendario, tarea, tareas (bandeja), dashboard, avisos |
| Crear/editar evento | calendario, dashboard, avisos |
| Papelera / restaurar | tareas, dashboard, calendario, proyectos |
| Proyectos / áreas | proyectos, tareas, dashboard |
| Configuración | config, dashboard, calendario, progreso |

Reglas: `staleTime` corto (30 s) en dashboard y avisos; refetch al enfocar la ventana; avisos se consultan al abrir la campana y cada 60 s (DTP-10, sin push).

## 11. Estructura de código (apps/web)

```
src/
  app/            providers, router, layout
  features/
    tareas/ calendario/ areas/ dashboard/ notificaciones/ progreso/ identidad/ configuracion/
      api/        cliente + esquemas Zod generados de OpenAPI
      hooks/      useTareas, useCambiarEstado, ...
      components/
      pages/
  shared/         ui/ (botón, chip, modal, toast), lib/ (fechas, formato)
```
Una feature no importa de otra; comparten solo `shared/`. Verificar con dependency-cruiser.

## 12. Del prototipo a React

| Prototipo (`prototipo.html`) | Producción |
|---|---|
| Objeto `S` en memoria | API + TanStack Query |
| Funciones de dominio (`cambiarEstado`, `bandeja`, `avisos`, `sugerir`, `sobrecarga`) | **Se mueven al backend**; el UI solo presenta |
| `render()` completo | componentes + cache |
| `data-a` / `data-form` | handlers de componentes |
| Hash routing | React Router |

Simplificaciones del prototipo respecto al SPEC: sin recurrencias ni series, una sola ventana de disponibilidad para lunes–viernes, zona horaria solo informativa, algoritmo de sugerencias simplificado, meta aplicada retroactivamente en la racha. No usarlo como referencia de reglas; la referencia es el SPEC.

## 13. Decisiones abiertas

1. Librería de UI (propuesta: componentes propios sobre Radix UI + CSS variables).
2. Componente de calendario (propuesta: construir vista propia; evaluar FullCalendar solo si el costo lo justifica).
3. Biblioteca de iconos.
4. Tema oscuro (fuera de alcance inicial).
5. Estrategia de i18n (solo español en I01–I08).

## 14. Orden de construcción sugerido (por incrementos)

I01 identidad + shell + captura → I02 tareas y estados → I03 áreas/proyectos → I04 calendario (eventos, bloques) → I05 avisos → I06 dashboard → I07 progreso → I08 configuración y endurecimiento. Cada incremento cierra con pruebas de componente y revisión de accesibilidad.
