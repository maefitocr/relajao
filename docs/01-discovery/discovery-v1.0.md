# RELAJAO — Discovery funcional v1.0 del MVP

> **Nombre de trabajo durante el Discovery:** DITSO (antes "Focus OS"). El repositorio y la marca actual son **RELAJAO**. En este documento, "DITSO" y "RELAJAO" se refieren al mismo producto.

| Campo | Valor |
|---|---|
| Versión | 1.0 |
| Estado | **CERRADO — línea base funcional del MVP** |
| Inicio del Discovery | 14 de noviembre de 2026 |
| Cierre formal | 15 de noviembre de 2026 |
| Autor de las decisiones | Jose Villegas (aprobación explícita en cada etapa) |
| Fuente | Registro de las sesiones de Discovery del producto (14–15 de noviembre de 2026) |
| Alcance de este documento | Solo definición funcional. **No incluye arquitectura, tecnologías ni implementación** (no autorizadas todavía). |

> **Nota de procedencia.** Este documento se reconstruyó a partir del registro completo de las sesiones de Discovery (132 intervenciones del responsable del producto y las especificaciones presentadas para aprobación). Todo lo que figura aquí fue propuesto y aprobado explícitamente en esa conversación. Lo que no se pudo recuperar con exactitud está marcado en la sección [12. Notas de reconstrucción](#12-notas-de-reconstrucción).

---

## Índice

1. [Resumen ejecutivo](#1-resumen-ejecutivo)
2. [Historial de aprobaciones](#2-historial-de-aprobaciones)
3. [Etapa 1 — Declaración del problema](#3-etapa-1--declaración-del-problema)
4. [Etapa 2 — Usuario objetivo](#4-etapa-2--usuario-objetivo)
5. [Etapa 3 — Funcionalidades del MVP (F01–F07)](#5-etapa-3--funcionalidades-del-mvp-f01f07)
6. [Etapa 4 — Exclusiones del MVP (E01–E12)](#6-etapa-4--exclusiones-del-mvp-e01e12)
7. [Etapa 5 — Criterios de éxito (S01–S10)](#7-etapa-5--criterios-de-éxito-s01s10)
8. [Cierre formal y reglas de la línea base](#8-cierre-formal-y-reglas-de-la-línea-base)
9. [Registro de solicitudes de cambio y ajustes de alcance](#9-registro-de-solicitudes-de-cambio-y-ajustes-de-alcance)
10. [Puntos abiertos y observaciones](#10-puntos-abiertos-y-observaciones)
11. [Siguientes etapas (sin iniciar)](#11-siguientes-etapas-sin-iniciar)
12. [Notas de reconstrucción](#12-notas-de-reconstrucción)
- [Apéndice A — Contexto previo (Focus OS)](#apéndice-a--contexto-previo-focus-os)
- [Apéndice B — Propuesta de gestión documental (no aprobada)](#apéndice-b--propuesta-de-gestión-documental-no-aprobada)
- [Apéndice C — Descripción sugerida para GitHub](#apéndice-c--descripción-sugerida-para-github)

---

## 1. Resumen ejecutivo

### Visión del producto

**RELAJAO es una aplicación de productividad personal que ayuda a organizar responsabilidades, planificar el tiempo y mantener la constancia sin generar sobrecarga innecesaria.**

Combina tres elementos:

- **Organización:** tareas, proyectos y áreas de vida en un solo lugar.
- **Planificación:** calendario, bloques de trabajo, disponibilidad y sugerencias ante conflictos.
- **Motivación:** progreso visible, metas, rachas y gamificación ligera.

El sistema recomienda alternativas, pero **el usuario conserva el control de sus decisiones**.

### Principio rector

> No busca que las personas hagan más cosas, sino que puedan organizarse mejor, avanzar en lo que realmente importa y reconocer sus logros sin sentirse abrumadas.

Filosofía de trabajo transversal: **Keep Simple**. Ante la duda, se pospone la capacidad avanzada para una iteración posterior.

### Cifras del Discovery

| Elemento | Resultado |
|---|---|
| Etapas aprobadas | 5 / 5 |
| Funcionalidades aprobadas | 7 / 7 (F01–F07) |
| Exclusiones aprobadas | 12 (E01–E12) |
| Criterios de éxito aprobados | 10 / 10 (S01–S10) |

### Funcionalidades aprobadas

| ID | Funcionalidad | Versión aprobada | Reglas de negocio | Criterios de aceptación |
|---|---|---|---|---|
| F01 | Gestión de tareas | v1.0 | RN-01 a RN-08 | CA-01 a CA-18 (18) |
| F02 | Calendario y planificación | v1.0 (basada en RC2) | Matriz D01–D43 | CA01 a CA27 (27) |
| F03 | Áreas de vida y proyectos | **v1.1** | RN-F03-58 a RN-F03-70 (y decisiones D01–D16) | CA-F03 (20 + 6 = 26) |
| F04 | Dashboard | **v1.16** | D01–D25, RN-F04-42 a RN-F04-49 | CA-F04-01 a CA-F04-22 (22) |
| F05 | Notificaciones y recordatorios | v1.0 | D01–D15 | CA-F05-01 a CA-F05-18 (18) |
| F06 | Progreso y motivación | v1.0 | RN-F06-01 a RN-F06-16 | CA-F06-01 a CA-F06-17 (17) |
| F07 | Configuración y preferencias | v1.0 | RN-F07-01 a RN-F07-16 | CA-F07-01 a CA-F07-17 (17) |

---

## 2. Historial de aprobaciones

| Fecha | Hito | Resultado |
|---|---|---|
| 14-nov-2026 | Etapa 1 — Declaración del problema v1.0 | Aprobada |
| 14-nov-2026 | Etapa 2 — Usuario objetivo v1.0 | Aprobada |
| 14-nov-2026 | F01 — Gestión de tareas v1.0 | Aprobada |
| 14-nov-2026 | F02 — Calendario y planificación v1.0 (RC2, 27 CA) | Aprobada |
| 14-nov-2026 | F03 — Áreas de vida y proyectos v1.0 (incluye P01 y P02, 20 CA) | Aprobada |
| 14/15-nov-2026 | F03 v1.1 (CR-F03-01 y CR-F03-02; RN-F03-64 a 70; CA-F03-21 a 26) | Aprobada |
| 15-nov-2026 | F04 — Dashboard v1.16 (con D25 y 22 CA) | Aprobada |
| 15-nov-2026 | F05 — Notificaciones y recordatorios v1.0 (D01–D15, 18 CA) | Aprobada |
| 15-nov-2026 | F06 — Progreso y motivación v1.0 (7 capacidades, D04 pospuesta) | Aprobada |
| 15-nov-2026 | F07 — Configuración y preferencias v1.0 (5 capacidades, 4 pospuestas) | Aprobada |
| 15-nov-2026 | Etapa 4 — Exclusiones E01–E12 | Aprobada |
| 15-nov-2026 | Etapa 5 — Criterios de éxito S01–S10 | Aprobada |
| 15-nov-2026 | **Cierre formal del Discovery funcional v1.0** | **Cerrado** |

> Las fechas de F03–F07 se ubican entre el 14 y el 15 de noviembre de 2026. Los mensajes de la conversación llevan marca de tiempo, pero no se transcribió la hora exacta de cada aprobación.

---

## 3. Etapa 1 — Declaración del problema

**Versión 1.0 · Aprobada**

### Planteamiento original del usuario

El usuario describió que quiere mejorar su desorden mental de tareas, trabajo, proyectos, cursos y proyectos personales, con el fin de generar más ingresos. Busca algo para personas como él que quieren unificar sus tareas, pero **no un simple sistema de tareas**: debe tener un sentido y un orden psicológico que ayude con la procrastinación y dé dopamina. Debe organizar un calendario realista con tareas de la vida cotidiana, trabajo y proyectos, y permitir visualizar de forma simple y ordenada cuándo uno genera muchos planes y se satura con cosas que no puede cumplir o que organiza mal.

- **Fuera de alcance en ese momento:** la conexión con un agente de IA.
- **Criterios de éxito mencionados:** módulos de creación de tareas y de calendario donde se organice todo; poder actualizar con los calendarios principales; no solo poner tareas sino completarlas y generar dopamina por ello. *(La sincronización con calendarios externos quedó después excluida del MVP; ver E01.)*

### Contexto

Las personas deben gestionar simultáneamente responsabilidades laborales, actividades cotidianas, compromisos personales, formación académica y proyectos de crecimiento personal y económico. La dispersión entre aplicaciones, calendarios, notas y pensamientos dificulta mantener una visión clara, establecer prioridades y organizar el tiempo. Como consecuencia aparecen sobrecarga mental, procrastinación, planificación poco realista y frustración.

### Problema central

Las herramientas tradicionales se enfocan en registrar, clasificar y completar actividades, pero no siempre ayudan a comprender la capacidad real de planificación, equilibrar las áreas de la vida ni mantener una motivación sostenible.

> Existe una desconexión entre lo que las personas desean lograr, lo que planifican y lo que realmente pueden ejecutar con el tiempo y los recursos disponibles.

### Propuesta de valor

RELAJAO busca ser un organizador personal integral que centralice responsabilidades, tareas, proyectos y objetivos en una experiencia visual simple, estructurada y motivadora. Debe ayudar a:

1. **Reducir la sobrecarga mental**, centralizando compromisos.
2. **Planificar de forma realista**, identificando sobrecargas y proponiendo alternativas sin quitarle el control al usuario.
3. **Equilibrar responsabilidades y aspiraciones** (cotidiano, trabajo, formación, proyectos personales).
4. **Fortalecer la motivación** con retroalimentación positiva, visualización del progreso y gamificación moderada.
5. **Promover la ejecución sostenible**, priorizando el cumplimiento realista sobre la acumulación de tareas.

### Decisiones de producto de la Etapa 1

| Dimensión | Decisión |
|---|---|
| Sobrecarga | Advertir y proponer redistribución, sin imponer restricciones |
| Motivación | Combinación equilibrada: progreso visual, celebraciones y gamificación |
| Propósito | Equilibrio entre vida cotidiana, trabajo y objetivos personales |
| Experiencia | Simple, clara y con mínima fricción |
| Filosofía | Progreso sostenible sobre productividad excesiva |

### Hipótesis de producto

Si una persona puede centralizar sus responsabilidades, planificarlas según su disponibilidad, recibir sugerencias ante posibles sobrecargas y visualizar positivamente sus avances, entonces podrá mejorar su organización, reducir la procrastinación y desarrollar mayor constancia. **Esta hipótesis debe validarse con uso real.**

### Salvaguarda de comunicación

El producto no debe tratar clínicamente la procrastinación ni prometer efectos psicológicos específicos. Se diseña una experiencia basada en principios de organización personal, motivación y refuerzo positivo.

---

## 4. Etapa 2 — Usuario objetivo

**Versión 1.0 · Aprobada**

### Decisiones de la Etapa 2

| Dimensión | Decisión |
|---|---|
| Público inicial | Personas con múltiples responsabilidades, sin limitar profesión |
| Experiencia tecnológica | Accesible a cualquier nivel |
| Frecuencia de uso | Uso diario con revisión semanal |

### Usuario objetivo principal

Personas que gestionan múltiples responsabilidades personales, laborales, académicas o profesionales y necesitan organizar sus compromisos de manera centralizada, realista y sostenible. El producto no se limita a una profesión ni a un nivel de experiencia tecnológica.

### Características del usuario

- **Responsabilidades múltiples:** combina actividades cotidianas, trabajo, estudio y proyectos personales.
- **Necesidad de claridad:** busca reducir la dispersión y visualizar prioridades.
- **Planificación imperfecta:** puede sobreestimar su disponibilidad.
- **Motivación variable:** necesita reconocer avances.
- **Diversidad tecnológica:** experiencia limitada o avanzada.

### Ciclos de uso (recomendados, no obligatorios)

- **Ciclo diario:** consultar actividades, identificar prioridades, actualizar compromisos, registrar avances y completar tareas.
- **Ciclo semanal:** revisar resultados, identificar pendientes y reorganizar la semana siguiente según la disponibilidad.

### Necesidades fundamentales

1. Centralizar tareas, compromisos y objetivos.
2. Visualizar el calendario de forma simple y ordenada.
3. Organizar actividades considerando el tiempo disponible.
4. Identificar sobrecargas y recibir sugerencias de redistribución.
5. Reconocer logros con retroalimentación positiva y gamificación equilibrada.
6. Mantener el control sobre decisiones y prioridades.
7. Usar la plataforma sin conocimientos técnicos especializados.

### Principios de experiencia de usuario

- **Simplicidad:** comprensible desde el primer uso.
- **Baja fricción:** registrar y completar actividades con el mínimo esfuerzo razonable.
- **Flexibilidad:** el usuario conserva el control de su planificación.
- **Progreso sostenible:** no se penaliza por descansar, reprogramar o interrumpir la rutina.
- **Claridad visual:** primero lo relevante, sin saturar la pantalla.

### Escenarios principales de uso

Inicio del día · Captura de pendientes · Planificación de actividades · Finalización y reconocimiento · Revisión semanal.

### Estrategia de validación

El fundador será el primer usuario de prueba, con responsabilidades y compromisos reales. Después se incorporarán usuarios con perfiles distintos. La validación inicial **no** se considera suficiente para demostrar que el producto funciona para todos los perfiles.

---

## 5. Etapa 3 — Funcionalidades del MVP (F01–F07)

### Orden inicial propuesto vs. resultado final

La Etapa 3 comenzó con una lista tentativa de siete funcionalidades (gestión de tareas, calendario, áreas y proyectos, dashboard, motivación y gamificación, revisión semanal, integraciones de calendario). Al avanzar el Discovery, la lista final aprobada quedó así:

| ID | Funcionalidad final |
|---|---|
| F01 | Gestión de tareas |
| F02 | Calendario y planificación |
| F03 | Áreas de vida y proyectos |
| F04 | Dashboard |
| F05 | Notificaciones y recordatorios |
| F06 | Progreso y motivación |
| F07 | Configuración y preferencias |

La revisión semanal quedó cubierta por el progreso semanal de F04 y el historial de siete días de F06. Las integraciones de calendario externas quedaron **excluidas del MVP** (E01).

---

### F01 — Gestión de tareas · v1.0

**Objetivo.** Permitir capturar, organizar, ejecutar y completar tareas personales, laborales y académicas desde un espacio centralizado, minimizando el esfuerzo de planificación y ofreciendo una experiencia sencilla y motivadora.

#### Decisiones del usuario

| Ronda | Decisión |
|---|---|
| 1 | **Captura:** bandeja de entrada para tareas sin planificar |
| 1 | **Duración:** estimación opcional |
| 1 | **Estados:** pendiente, en progreso, pausada, completada y cancelada |
| 2 | **Subtareas:** permitir subtareas simples desde el MVP |
| 2 | **Recurrencia:** básicas diarias, semanales y mensuales |
| 2 | **Finalización:** completar directamente desde cualquier estado activo |
| 3 | **Completar con subtareas pendientes:** completar automáticamente las subtareas restantes |
| 3 | **Editar recurrencias:** permitir editar solo una ocurrencia o las futuras |
| 3 | **Eliminación:** papelera con recuperación |

#### Alcance funcional

| ID | Capacidad | Comportamiento |
|---|---|---|
| F01.01 | Captura rápida | Crear tarea únicamente con título |
| F01.02 | Bandeja de entrada | Mostrar tareas no planificadas |
| F01.03 | Información de tarea | Descripción, prioridad y duración opcionales |
| F01.04 | Gestión de estados | Cinco estados operativos |
| F01.05 | Subtareas | Crear, editar, completar y eliminar |
| F01.06 | Recurrencias | Diarias, semanales y mensuales |
| F01.07 | Edición de recurrencias | Una ocurrencia o todas las futuras |
| F01.08 | Finalización | Completar directamente desde estados activos |
| F01.09 | Progreso | Registrar finalización y mostrar reconocimiento |
| F01.10 | Papelera | Eliminación lógica y recuperación |
| F01.11 | Persistencia | Conservar tareas y cambios entre sesiones |

#### Reglas de negocio

- **RN-01 · Creación.** El título es obligatorio y no puede contener solo espacios. La tarea nueva inicia en *Pendiente*. Los demás campos son opcionales.
- **RN-02 · Bandeja de entrada.** Toda tarea sin planificación aparece en la bandeja. La bandeja es una vista, no un estado. Una tarea puede existir sin fecha ni duración.
- **RN-03 · Estados.** *Pendiente, En progreso, Pausada, Completada y Cancelada.* Se puede completar directamente desde cualquiera de los tres estados activos. Las completadas pueden reabrirse como pendientes; las canceladas pueden reactivarse como pendientes.
- **RN-04 · Subtareas.** Un solo nivel; cada subtarea tiene título y estado simple (pendiente o completada). Al completar la tarea principal, todas las subtareas pendientes se completan automáticamente. Completar todas las subtareas **no** completa automáticamente la tarea principal.
- **RN-05 · Recurrencias.** Diarias, semanales y mensuales. Cada ocurrencia conserva su propio estado y registro de cumplimiento. Se puede modificar una ocurrencia individual o la serie futura sin alterar el historial anterior.
- **RN-06 · Finalización y progreso.** Completar registra fecha y hora, actualiza el estado y muestra retroalimentación positiva. Una tarea cancelada no cuenta como completada ni genera reconocimiento.
- **RN-07 · Eliminación lógica.** Eliminar traslada la tarea a la papelera; se puede restaurar conservando información y relaciones. La eliminación definitiva no forma parte del flujo habitual del MVP.
- **RN-08 · Persistencia.** Tareas, subtareas, recurrencias, estados y fechas de finalización se conservan entre sesiones.

#### Criterios de aceptación

| ID | Escenario | Resultado esperado |
|---|---|---|
| CA-01 | Crear tarea solo con título | Se guarda pendiente y sin fecha |
| CA-02 | Crear tarea con título vacío | Se rechaza y muestra validación |
| CA-03 | Consultar bandeja de entrada | Se muestran tareas sin planificar |
| CA-04 | Editar atributos opcionales | Los cambios persisten |
| CA-05 | Cambiar estado | Se refleja el nuevo estado |
| CA-06 | Completar desde pendiente o pausada | Se completa sin pasos intermedios |
| CA-07 | Completar tarea principal con subtareas pendientes | Todas quedan completadas |
| CA-08 | Completar todas las subtareas | La tarea principal conserva su estado |
| CA-09 | Crear recurrencia diaria, semanal o mensual | Se generan las ocurrencias correspondientes |
| CA-10 | Completar una ocurrencia | Las demás no cambian |
| CA-11 | Editar una ocurrencia | No modifica las restantes |
| CA-12 | Editar ocurrencias futuras | El historial anterior permanece intacto |
| CA-13 | Completar tarea | Se registra fecha/hora y reconocimiento visual |
| CA-14 | Reabrir tarea completada | Vuelve a pendiente sin duplicarse |
| CA-15 | Cancelar tarea | No se contabiliza como logro |
| CA-16 | Eliminar tarea | Se mueve a la papelera |
| CA-17 | Restaurar tarea | Recupera información y relaciones |
| CA-18 | Cerrar y volver a ingresar | Los cambios permanecen guardados |

> Estos criterios describen pruebas que deberán cumplirse al implementar. No son pruebas ejecutadas.

#### Fuera de alcance de F01

Subtareas anidadas en varios niveles · dependencias entre tareas · automatizaciones con agentes de IA · reglas de recurrencia avanzadas · colaboración y asignación a otras personas · puntos, niveles e insignias avanzados · sincronización con calendarios externos.

#### Observaciones registradas (no bloqueantes)

- **Subtareas completadas automáticamente:** se recomendó distinguir internamente las finalizaciones automáticas de las manuales para mantener trazabilidad.
- **Recurrencias mensuales (días 29, 30, 31):** se propuso usar el último día disponible del mes. **No quedó decidido formalmente** (ver sección 10).

---

### F02 — Calendario y planificación · v1.0 (RC2)

**Principio de producto:** *planificar tiempo, no fiscalizar tiempo.* El MVP no registra minutos realmente trabajados, no exige confirmar cada sesión ni mantiene auditoría exhaustiva de actividad.

**Propósito.** Organizar compromisos y reservar tiempo para realizar tareas mediante un calendario diario, semanal y mensual que advierte conflictos y ofrece sugerencias de planificación.

#### Modelo conceptual

- **Tareas y subtareas (F01):** estados, prioridades, duración estimada y recurrencias.
- **Bloques:** reservas de tiempo para tareas específicas. Un bloque **reserva tiempo; no crea otra tarea**.
- **Eventos:** compromisos únicos o recurrentes.
- La planificación y el estado de una tarea son **independientes**. Un bloque pasado no demuestra que la tarea se realizó.

#### Decisiones del usuario por ronda

| Ronda | Decisiones |
|---|---|
| 1 | Planificación **híbrida** (el usuario planifica y RELAJAO sugiere espacios) · Vistas diaria, semanal y mensual · Una tarea puede distribuirse en varios bloques |
| 2 | Disponibilidad: horarios habituales configurables + excepciones por día · Detectar superposición y exceso de capacidad · Redistribución: sugerir alternativas y pedir confirmación |
| (aclaración) | Para dividir tareas largas en sesiones: **subtareas** |
| 3 | Descansos y márgenes configurables con valores recomendados · Orden de sugerencias: equilibrar prioridad, fecha límite y áreas de vida · Tareas no realizadas: advertir y proponer reprogramación · Sesiones configurables con división sugerida |
| 4 | Compromisos fijos: no moverlos en sugerencias automáticas salvo modificación explícita · Distinguir fecha límite de fecha de ejecución · Conflictos manuales: advertir y permitir guardar · Eventos de calendarios externos ocupan disponibilidad y no se modifican desde sugerencias |
| 5 | Bloques no ejecutados: conservar historial y proponer nuevo bloque · Fechas límite vencidas: advertir y permitir reprogramar · Trabajo parcial: registrar tiempo trabajado y mantener pendiente lo restante *(luego pospuesto por Keep Simple)* · Programar subtareas individualmente |
| 6 | Tiempo restante calculado con ajuste manual *(pospuesto)* · Registro manual de minutos *(pospuesto)* · Sugerencias individuales de horarios · MVP esencial y capacidades avanzadas en iteraciones posteriores |
| 7 | Recurrencia de eventos: diaria, semanal y mensual · Eliminación de bloques: conservar historial y permitir eliminar planificación futura · Zona horaria del usuario · Sobrecarga: advertir y sugerir sin impedir guardar |
| 8 | Edición de eventos recurrentes: una ocurrencia o todas las futuras, preservando historial · Registros de tiempo independientes de bloques *(pospuesto)* · F02 funciona con eventos locales; los externos se agregarían después |
| 9 | Tiempo real mayor al estimado: permitirlo y mostrar desviación *(pospuesto)* · Registrar tiempo no completa la tarea · Planificar tareas sin área asignada |
| 10 | Alcance del primer MVP: **P0 y P1 incluidos**, entregados incrementalmente · Eventos recurrentes en P1 · Registro manual de tiempo e historial en P1 *(el tiempo real luego se pospuso)* |
| D38 | Modelo simple: tareas y eventos recurrentes; **bloques sin recurrencia propia** |
| D39 | Horario habitual opcional con sugerencias de bloques y confirmación del usuario |
| D40 | **Keep Simple:** duración estimada opcional, bloques y estados; posponer medición de tiempo real y cálculos derivados |
| D41 | Sugerir eliminar bloques futuros de tareas completadas o canceladas, con confirmación |
| D42 | Conservar bloques pasados como reservas históricas y sugerir reprogramación si la tarea sigue pendiente, **sin inferir ejecución** |
| D43 | Conservar bloques de tareas eliminadas lógicamente, ocultarlos del calendario activo y restaurarlos con advertencia de conflictos |
| OBS-F02-01 | Eliminar eventos recurrentes: dos opciones, **esta ocurrencia** o **toda la serie**, conservando historial mínimo de las pasadas |

El usuario cuestionó la complejidad del seguimiento de tiempo ("¿no se ve complicado añadir tiempo a las tareas? Keep simple") y pidió aclarar la diferencia entre bloques, subtareas y tareas recurrentes. Esto llevó a las decisiones D38–D40.

#### Alcance funcional

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

#### Reglas de negocio consolidadas

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

La duración de un bloque sale de su inicio y fin y representa **tiempo reservado**, no trabajado.

#### Criterios de aceptación (27)

**A. Calendario y programación · P0**

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

**B. Planificación inteligente · P1**

| ID | Criterio |
|---|---|
| CA09 | Detecta planificación superior a la disponibilidad, advierte y permite guardar manualmente |
| CA10 | El usuario configura descansos y márgenes; las sugerencias los respetan sin requerir registro de ejecución |
| CA11 | Una sugerencia individual considera disponibilidad, prioridad, fecha límite y área de vida si existe; funciona sin F03 |
| CA12 | Una redistribución sugerida no modifica reservas hasta que el usuario confirme |
| CA13 | Las sugerencias no mueven compromisos definidos como fijos |

**C. Recurrencia y prevención de duplicados · P1**

| ID | Criterio |
|---|---|
| CA14 | El usuario crea eventos recurrentes diarios, semanales y mensuales |
| CA15 *(actualizado por OBS-F02-01)* | El usuario puede editar una ocurrencia o esta y las futuras, preservando excepciones y eventos pasados. Para eliminar, puede seleccionar únicamente la ocurrencia actual o toda la serie. Eliminar toda la serie retira sus eventos del calendario activo, conservando el historial mínimo de las ocurrencias pasadas |
| CA16 | Un bloque puede vincularse a una ocurrencia recurrente específica sin crear otra tarea |
| CA17 | El horario habitual de una tarea recurrente es opcional; aceptar una sugerencia crea el bloque y rechazarla no cambia nada |
| CA18 | Un doble clic o reintento de confirmación no crea duplicados; el usuario puede crear intencionalmente otra sesión |

**D. Historial, cierre y restauración · P1**

| ID | Criterio |
|---|---|
| CA19 | Los bloques pasados permanecen consultables como reservas, sin marcarse como realizados o incumplidos |
| CA20 | Reprogramar una tarea pendiente conserva el bloque pasado y crea una reserva futura sin duplicar la tarea |
| CA21 | Al completar o cancelar una tarea, se sugiere liberar bloques futuros asociados (incluidos los de subtareas); aceptar elimina los seleccionados y rechazar conserva todos |
| CA22 | Los bloques de una tarea eliminada lógicamente se ocultan del calendario activo y no consumen disponibilidad |
| CA23 | Restaurar una tarea recupera sus bloques vinculados y advierte conflictos, sin mover reservas ajenas |

**E. Integridad transversal · P0/P1**

| ID | Criterio |
|---|---|
| CA24 | La fecha límite permanece separada de la programación; si vence, se advierte sin cambiar el estado y se permite reprogramar |
| CA25 | Los horarios se crean, guardan y visualizan respetando la zona horaria configurada |
| CA26 | Los bloques no admiten recurrencia propia y la programación de ocurrencias recurrentes no genera tareas duplicadas |
| CA27 *(actualizado por OBS-F02-01)* | El usuario puede editar o eliminar bloques futuros sin borrar reservas históricas. Eliminar una ocurrencia recurrente no elimina las demás; eliminar toda la serie no borra el historial mínimo de sus ocurrencias pasadas. Ninguna de estas acciones modifica automáticamente los estados de las tareas vinculadas |

#### Matriz de trazabilidad D01–D43

Leyenda: **C** cubierta · **A** ajustada por Keep Simple · **P** pospuesta · **S** sustituida · **F** contrato futuro.

| Decisión | Est. | Cobertura | Decisión | Est. | Cobertura |
|---|---|---|---|---|---|
| D01 Planificación híbrida | C | CA11–12 | D23 Eventos recurrentes | C | CA14 |
| D02 Vistas de calendario | C | CA01 | D24 Eliminación de bloques futuros | A | CA21, CA27 |
| D03 Varios bloques | C | CA03 | D25 Zona horaria | C | CA25 |
| D04 Disponibilidad | C | CA05 | D26 Sobrecarga con advertencia | C | CA09 |
| D05 Superposiciones/capacidad | C | CA06, CA09 | D27 Edición de recurrencias | C | CA15 |
| D06 Confirmar redistribución | C | CA12 | D28 Registros independientes de tiempo | P | Fuera MVP |
| D07 Descansos y márgenes | C | CA10 | D29 Sin dependencia externa | C | CA08 |
| D08 Equilibrio de prioridades | C | CA11 | D30 Tiempo real mayor al estimado | P | Fuera MVP |
| D09 Pendientes sin completar | A | CA19–20 | D31 Tiempo no completa tareas | S | CA07 |
| D10 Sesiones configurables | A | CA03, CA10 | D32 Área de vida opcional | C | CA08, CA11 |
| D11 Compromisos fijos | C | CA13 | D33 P0+P1 dentro del MVP | C | Alcance |
| D12 Fecha límite independiente | C | CA24 | D34 Recurrencia de eventos P1 | C | CA14 |
| D13 Conflictos manuales | C | CA06 | D35 Registro de tiempo P1 | S | D40 |
| D14 Eventos externos protegidos | F | F07 (ver nota) | D36 Agregación de minutos | P | Fuera MVP |
| D15 Historial y reprogramación | C | CA19–20 | D37 Minutos directos y de subtareas | P | Fuera MVP |
| D16 Fecha límite vencida | C | CA24 | D38 Bloques sin recurrencia | C | CA26 |
| D17 Minutos parciales | P | Fuera MVP | D39 Horario habitual sugerido | C | CA17 |
| D18 Subtareas programables | C | CA04 | D40 Keep Simple | C | Alcance |
| D19 Tiempo restante calculado | P | Fuera MVP | D41 Liberar bloques futuros | C | CA21 |
| D20 Registro manual de minutos | P | Fuera MVP | D42 Historial sin inferir ejecución | C | CA19–20 |
| D21 Sugerencias individuales | C | CA11 | D43 Papelera y restauración | C | CA22–23 |
| D22 Alcance esencial y avanzado | C | P0/P1 | | | |

Desglose: 30 cubiertas, 3 ajustadas, 7 pospuestas, 2 sustituidas, 1 contrato futuro (total 43).

> **Nota sobre D14:** la matriz remite a "F07" como contrato futuro para eventos externos. Al cierre del Discovery, F07 quedó como *Configuración y preferencias* y las integraciones externas están excluidas (E01). En la práctica, el manejo de calendarios externos queda fuera del MVP.

#### Fuera de alcance de F02

Medición de minutos trabajados · cronómetro y cálculo de tiempo restante · recurrencia propia de bloques · planificación automática de varios días · optimización avanzada por patrones · integraciones externas obligatorias.

---

### F03 — Áreas de vida y proyectos · v1.1

**Jerarquía:** Área → Proyecto → Tareas. Las tareas pueden pertenecer a un proyecto, directamente a un área, o quedar sin clasificación.

#### Decisiones del usuario

| ID | Decisión |
|---|---|
| D01 | Estructura simple: área → proyecto → tareas, permitiendo tareas sin proyecto |
| D02 | Asociación directa: tareas pueden pertenecer a un área sin proyecto o permanecer sin área |
| D03 | Áreas sugeridas y personalizables *(ajustado por D04 y D12)* |
| D04 | **Ajuste del usuario:** no implementar la eliminación de áreas en la primera versión. Las áreas son **predefinidas, no se pueden eliminar**, pero sí cambiar nombre o color. Se revisará más adelante (Keep Simple) |
| D05 | Proyecto básico: nombre obligatorio, descripción opcional, área obligatoria y progreso derivado de tareas completadas |
| D06 | Excluir tareas canceladas del progreso: completadas ÷ tareas no canceladas |
| D07 | Proyectos sin tareas válidas muestran 0 %, sin considerarse completados automáticamente |
| D08 | Gestión básica: crear, editar y eliminar proyectos; al eliminar, sus tareas quedan asociadas directamente al área |
| D09 | Herencia automática: al cambiar el área del proyecto, sus tareas heredan la nueva área sin modificar estados ni bloques |
| D10 | Movimiento libre de tareas entre proyectos, áreas directas o sin clasificación, conservando estados, subtareas y reservas |
| D11 | Lista jerárquica de áreas, proyectos y tareas, con filtros por área y proyecto, sin dashboards adicionales |
| D12 | **Cinco áreas predefinidas:** Trabajo, Salud, Finanzas, Desarrollo personal y Vida personal |
| D13 | Solo cuentan las tareas principales para el progreso; las subtareas no suman por separado |
| D14 | Excluir las tareas recurrentes del cálculo de progreso (siguen asociadas al proyecto) |
| D15 | Mostrar tiempo estimado total y pendiente por proyecto, calculado desde las tareas, sin medir tiempo real |
| D16 | Cálculo simple: solo tareas principales no recurrentes ni canceladas; subtareas excluidas; tareas sin estimación aportan cero |

Sobre el tiempo en proyectos, el usuario preguntó si los proyectos son diarios, semanales o de otro tipo; se aclaró que **los proyectos no administran tiempo directamente** (el tiempo viene de las tareas y de F02). El usuario respondió "no" a incorporar periodicidad de proyectos.

#### Precisiones técnicas aprobadas con v1.0

- **P01 — Tareas eliminadas lógicamente:** dejan de participar en el progreso y los tiempos del proyecto; si se restauran, vuelven a participar según su estado y clasificación; eliminar no es lo mismo que cancelar.
- **P02 — Tareas recurrentes en proyectos:** pueden asociarse a un proyecto y se muestran en su lista identificadas como recurrentes; ni la serie ni sus ocurrencias contribuyen al progreso o resumen de tiempo; sus reservas siguen gestionándose en F02.

#### Reglas de cálculo

- **Progreso** = tareas principales completadas ÷ tareas principales elegibles × 100.
- **Tiempo total** = suma de estimaciones de tareas principales elegibles (cualquier estado de ejecución).
- **Tiempo pendiente** = suma de estimaciones de tareas elegibles en estado pendiente, en progreso o pausada. *No representa horas restantes reales*: una tarea de 6 h en progreso conserva sus 6 h hasta completarse.
- **Tarea elegible:** no es recurrente, no está cancelada y no está eliminada lógicamente.
- Sin tareas elegibles: progreso = 0 %.

Ejemplo ilustrativo del proyecto: tareas de 4 h (completada), 6 h (en progreso), 8 h (pendiente), 1 h recurrente (excluida) y 2 h cancelada (excluida) → progreso 33,3 %, tiempo total 18 h, pendiente 14 h.

#### Reglas complementarias

| Código | Regla |
|---|---|
| RN-F03-58 | Las tareas eliminadas lógicamente se excluyen de los indicadores activos |
| RN-F03-59 | Restaurar una tarea recalcula los indicadores correspondientes |
| RN-F03-60 | Las tareas recurrentes permanecen visibles dentro de sus proyectos |
| RN-F03-61 | Las ocurrencias recurrentes conservan su independencia según F01 |
| RN-F03-62 | Las reservas asociadas siguen gestionándose exclusivamente mediante F02 |
| RN-F03-63 | Los proyectos conservan una identidad estable aunque cambien de nombre o área |

#### Criterios de aceptación F03 v1.0 (20)

**Áreas y clasificación**
1. Existen cinco áreas iniciales con nombre y color editables.
2. No se permite crear, archivar ni eliminar áreas.
3. Una tarea puede tener proyecto, área directa o ninguna clasificación.
4. Las tareas de un proyecto heredan su área.

**Proyectos y movimientos**
5. Se pueden crear proyectos con nombre y área obligatorios.
6. Se pueden editar nombre, descripción y área.
7. Eliminar un proyecto conserva sus tareas asociadas directamente al área anterior.
8. Las tareas pueden moverse entre proyectos o quedar fuera de ellos.
9. Los movimientos preservan estados, subtareas, fechas, recurrencias y bloques.
10. Cambiar el área de un proyecto actualiza la clasificación de sus tareas.

**Indicadores**
11. El progreso se calcula con tareas principales elegibles.
12. Las subtareas no cuentan individualmente.
13. Las tareas recurrentes, canceladas y eliminadas lógicamente no cuentan.
14. Un proyecto sin tareas elegibles muestra 0 %.
15. Se muestran tiempo total y pendiente estimados.
16. Las tareas sin estimación aportan 0 h.
17. Completar, cancelar, restaurar o mover tareas recalcula los indicadores.

**Experiencia y persistencia**
18. La lista jerárquica permite navegar y filtrar por área o proyecto.
19. Las tareas recurrentes siguen visibles y sus ocurrencias conservan las reglas de F01.
20. Los cambios persisten y no alteran las reglas aprobadas de F01 y F02.

#### Ampliación v1.1 (CR-F03-01 y CR-F03-02)

Solicitada por el usuario durante F04 ("agreguemos prioridad en los proyectos, y un tag de favorito para anclar los prioritarios").

| Código | Regla |
|---|---|
| RN-F03-64 | Cada proyecto tiene una prioridad editable (Alta, Media o Baja; valor inicial **Media**) |
| RN-F03-65 | Cada proyecto puede marcarse o desmarcarse como **favorito** (valor inicial: no) |
| RN-F03-66 | Prioridad y favorito son propiedades independientes |
| RN-F03-67 | Modificarlas no cambia estados, prioridades ni fechas de sus tareas |
| RN-F03-68 | Los cambios se conservan entre sesiones |
| RN-F03-69 | Ordenar proyectos por prioridad descendente (Alta → Media → Baja) |
| RN-F03-70 | Empates resueltos alfabéticamente por nombre |

| Código | Criterio de aceptación adicional |
|---|---|
| CA-F03-21 | Al crear un proyecto, su prioridad inicial es Media y no es favorito |
| CA-F03-22 | Se puede modificar la prioridad sin afectar las tareas |
| CA-F03-23 | Se puede marcar o desmarcar un proyecto como favorito |
| CA-F03-24 | Los proyectos se ordenan por prioridad descendente y alfabéticamente en caso de empate |
| CA-F03-25 | Prioridad y favorito persisten entre sesiones |
| CA-F03-26 | Cambiar prioridad o favorito no altera progreso, fechas ni bloques de calendario |

La prioridad del proyecto **no** modifica la prioridad de sus tareas ni reordena bloques en F02.

#### Fuera de alcance de F03

Crear, eliminar o archivar áreas · archivar proyectos · estados manuales de proyecto · proyectos diarios/semanales/mensuales · fechas de inicio o fin de proyecto · cronómetros y horas reales · gráficos avanzados · dependencias entre proyectos o tareas.

---

### F04 — Dashboard · v1.16

**Enfoque:** Dashboard **híbrido** que combina planificación diaria y progreso personal, con prioridad en *lo que debo hacer hoy*.

#### Decisiones del usuario

| ID | Decisión |
|---|---|
| D01 | Dashboard híbrido (planificación diaria + progreso personal), prioridad en lo que se debe hacer hoy |
| D02 | Vista equilibrada: tareas de hoy, agenda, vencidas, alertas de sobrecarga, captura rápida y resumen compacto del progreso |
| D03 | "Tareas de hoy" = tareas con bloque hoy + tareas con fecha límite hoy, sin duplicados |
| D04 | Lista accionable de tareas vencidas con indicador de atraso y opciones para abrir, completar o pedir sugerencia de reprogramación (F02) |
| D05 | ~~Panel preventivo avanzado con análisis semanal, proyecciones y recomendaciones~~ → **sustituido por D25** |
| D06 | Proyección de carga limitada a la semana actual *(luego acotada por D25: sin proyecciones ni cálculos agregados)* |
| D07 | Progreso diario y semanal: completadas hoy, completadas esta semana y resumen de avance de proyectos activos |
| D08 | Mostrar proyectos con al menos una tarea principal elegible pendiente; los demás siguen accesibles en F03 |
| D09 | Orden contextual: bloques en curso y próximos, luego bloques posteriores, y al final tareas que vencen hoy sin horario; mostrar prioridad y fecha límite sin alterar F02 |
| D10 | Ventana fija de **120 minutos** para identificar bloques próximos |
| D11 | Acciones esenciales: abrir detalle, completar, iniciar o pausar (F01) y pedir sugerencias de reprogramación (F02) |
| D12 | Tareas completadas hoy en una sección secundaria contraíble |
| D13 | Captura rápida: **título obligatorio** + propiedades opcionales (prioridad, fecha límite, área) sin salir del Dashboard y sin exigir planificación |
| D14 | Línea de tiempo diaria por horas, diferenciando compromisos fijos y bloques de tareas |
| D15 | Mostrar eventos, bloques y espacios disponibles (F02), con opción de pedir sugerencias |
| D16 | Planificación manual al seleccionar espacios libres, con confirmación |
| D17 | Panel preventivo expandible con conflictos, causas y recomendaciones *(simplificado por D25)* |
| D18 | Análisis avanzado de carga semanal → **pospuesto a la versión v2** |
| D19 | Alertas con contexto: conflictos, elementos involucrados y opción de pedir alternativas (F02) |
| D20 | Estado vacío básico con mensajes sencillos |
| D21 | Actualización al abrir el Dashboard y después de acciones del usuario que afecten tareas, agenda, progreso o alertas |
| D22 | Distribución fija y adaptable a distintas pantallas, sin reorganización de componentes |
| D23 | Hasta cinco tareas vencidas iniciales, ordenadas por mayor atraso, con contador total y opción "ver todas" |
| D24 | Indicador de carga sencillo |
| D25 | **Panel preventivo expandible simplificado**, reutilizando conflictos, causas y alternativas de F02, **sin proyecciones semanales nuevas**. Ajusta D05/D17 |

**Contexto de la decisión D25.** El usuario expresó que el sistema crecía mucho ("quiero un sistema Keep Simple... un software desplegado inicialmente y luego ir añadiendo mejoras") y pidió pasar a v2 únicamente el análisis avanzado de carga semanal. También pidió terminar primero las funcionalidades y dejar para después las decisiones arquitectónicas, cuestionando una propuesta prematura de arquitectura monolítica.

**Límite funcional:** el Dashboard consulta y presenta información de F02. No implementa un segundo motor de planificación.

#### Reglas asociadas a favoritos y orden (derivadas de F03 v1.1)

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

#### Precisiones aprobadas

- **P01 — Conflictos semanales:** el panel puede mostrar conflictos detectados por F02 en la semana actual, pero no calcula porcentajes de ocupación, pronósticos ni recomendaciones nuevas por carga agregada.
- **P02 — Actualización:** la información se refresca tras una operación confirmada; si una operación falla, no se muestra como completada o guardada.

#### Criterios de aceptación (22)

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

---

### F05 — Notificaciones y recordatorios · v1.0

**Objetivo.** Que el usuario identifique tareas próximas a vencer, tareas vencidas y eventos próximos mediante **avisos internos**, sin depender de notificaciones externas. Sencilla, relevante y sin acumulación de avisos innecesarios.

*Nota de proceso:* tras varias rondas, el usuario expresó que el método de decidir una por una se estaba haciendo largo y cansado. Se pasó a un **formulario consolidado** con todas las decisiones de F05.

#### Decisiones (D01–D15)

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
| D11 | Marcar todos | Incluir acción global "Marcar todos como leídos" (solicitada por el usuario) |
| D12 | Sin fecha límite | No generar avisos, aunque tengan bloques planificados |
| D13 | Cambio de fecha límite | Retirar el aviso anterior y generar uno nuevo sin leer cuando corresponda |
| D14 | Transición a vencida | Sustituir el aviso de proximidad por uno nuevo de vencimiento, sin leer |
| D15 | Ausencia de varios días | Mostrar solo avisos vigentes (opción recomendada, confirmada en el formulario) |

#### Criterios de aceptación (18)

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

**Fuera de alcance de F05:** notificaciones push, correo, avisos del navegador, personalización de anticipaciones, posponer avisos, historial de notificaciones, resúmenes de ausencia y recordatorios por bloques de trabajo.

---

### F06 — Progreso y motivación · v1.0

El usuario eligió **incluir rachas, puntos e insignias**, lo que amplió F06; por eso se propuso una versión mínima de gamificación. Los valores numéricos fueron propuestos por el asistente y **aprobados explícitamente por el usuario** junto con F06.

#### Capacidades

| ID | Capacidad | Decisión |
|---|---|---|
| D01 | Resumen de logros (hoy y semana) | Incluir en MVP |
| D02 | Meta diaria opcional (cantidad de tareas) | Incluir en MVP |
| D03 | Progreso hacia la meta | Incluir en MVP |
| D04 | Reconocimiento de logros (mensajes) | **Pospuesto** |
| D05 | Rachas de constancia | Incluir en MVP |
| D06 | Insignias y puntos | Incluir en MVP |
| D07 | Historial semanal (últimos siete días) | Incluir en MVP |
| D08 | Sin penalizaciones | Incluir en MVP |

#### Reglas de negocio

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
| RN-F06-10 | **10 puntos por tarea principal completada**, sin duplicarlos al consultar de nuevo |
| RN-F06-11 | **Tres insignias iniciales:** primera tarea completada, primera meta diaria alcanzada y racha de 3 días |
| RN-F06-12 | Se conservan puntos e insignias aunque se interrumpa una racha |
| RN-F06-13 | Mostrar los últimos siete días de actividad, incluidos los días con cero tareas |
| RN-F06-14 | Actualizar indicadores cuando cambie una finalización; evitar puntos o logros duplicados |
| RN-F06-15 | Sin penalizaciones, puntuaciones negativas, comparaciones entre usuarios ni notificaciones motivacionales |
| RN-F06-16 | Mostrar los indicadores en una sección compacta del Dashboard (F04), sin duplicar el progreso de proyectos de F03 |

**Sin tienda de recompensas, niveles, rankings ni catálogo ampliable de insignias** en el MVP.

#### Criterios de aceptación (17)

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

---

### F07 — Configuración y preferencias · v1.0

Configuración centralizada y sencilla, que reutiliza lo ya aprobado en F02 y F06.

#### Capacidades

| ID | Capacidad | Decisión | Alcance |
|---|---|---|---|
| D01 | Perfil básico | Incluir | Consultar y editar el nombre visible |
| D02 | Zona horaria | Incluir | Consultar y modificar la zona horaria |
| D03 | Disponibilidad habitual | Incluir | Acceso a horarios, excepciones y descansos de F02 |
| D04 | Meta diaria | Incluir | Consultar, modificar o desactivar la meta de F06 |
| D05 | Apariencia (claro/oscuro) | **Pospuesto** | — |
| D06 | Preferencias de avisos | **Pospuesto** | — |
| D07 | Exportación de datos | **Pospuesto** | — |
| D08 | Gestión de cuenta | Incluir | Ver información básica de la cuenta y cerrar sesión |
| D09 | Restablecimiento de preferencias | **Pospuesto** | — |

#### Reglas de negocio

| Código | Regla |
|---|---|
| RN-F07-01 | Sección centralizada de configuración |
| RN-F07-02 | El perfil muestra el nombre visible y permite modificarlo |
| RN-F07-03 | El nombre visible no puede guardarse vacío ni solo con espacios |
| RN-F07-04 | Los cambios del perfil requieren una acción explícita de guardar |
| RN-F07-05 | Consultar y modificar la zona horaria |
| RN-F07-06 | Fechas y horas se interpretan según las reglas de zona horaria de F02 |
| RN-F07-07 | Cambiar la zona horaria no modifica automáticamente estados de tareas o eventos |
| RN-F07-08 | Acceso a disponibilidad habitual, excepciones y descansos de F02 |
| RN-F07-09 | Las modificaciones de disponibilidad siguen las validaciones de F02 |
| RN-F07-10 | Consultar, modificar o desactivar la meta diaria de F06 |
| RN-F07-11 | Progreso y rachas se calculan según F06, sin un segundo sistema de metas |
| RN-F07-12 | Consultar información básica de la cuenta |
| RN-F07-13 | Cerrar sesión mediante acción explícita |
| RN-F07-14 | Cerrar sesión no elimina ni modifica tareas, proyectos, eventos o preferencias |
| RN-F07-15 | Las preferencias guardadas permanecen al volver a iniciar sesión |
| RN-F07-16 | Sin ajustes de apariencia, avisos, exportación ni restablecimiento global en el MVP |

#### Criterios de aceptación (17)

| Código | Criterio |
|---|---|
| CA-F07-01 | Abrir Configuración desde la navegación principal |
| CA-F07-02 | El nombre visible actual aparece en el perfil |
| CA-F07-03 | Modificar y guardar un nombre visible válido |
| CA-F07-04 | No se permite guardar un nombre vacío o solo con espacios |
| CA-F07-05 | La zona horaria actual se muestra en Configuración |
| CA-F07-06 | Modificar y guardar la zona horaria |
| CA-F07-07 | Los cambios de zona horaria respetan las reglas temporales de F02 |
| CA-F07-08 | Acceder a horarios habituales, excepciones y descansos |
| CA-F07-09 | La edición de disponibilidad usa las reglas y validaciones de F02 |
| CA-F07-10 | Consultar la meta diaria vigente |
| CA-F07-11 | Modificar o desactivar la meta diaria |
| CA-F07-12 | Los indicadores de progreso y rachas reflejan la configuración de F06 |
| CA-F07-13 | Consultar información básica de la cuenta |
| CA-F07-14 | Cerrar sesión explícitamente |
| CA-F07-15 | Al cerrar sesión, datos y preferencias se conservan |
| CA-F07-16 | Las preferencias guardadas se mantienen al volver a iniciar sesión |
| CA-F07-17 | La configuración del MVP no presenta controles de apariencia, avisos, exportación ni restablecimiento global |

> **Nota de consistencia:** la gestión de cuenta presupone una sesión autenticada. Los mecanismos de autenticación y seguridad **no** se seleccionan aquí; se definirán después del Discovery.

---

## 6. Etapa 4 — Exclusiones del MVP (E01–E12)

**Aprobadas explícitamente, sin observaciones.** Todas se mantienen fuera del MVP. No eliminan las capacidades básicas ya aprobadas (por ejemplo, F02 conserva las sugerencias de planificación y F06 conserva puntos, rachas y las tres insignias iniciales).

| ID | Exclusión | Alcance excluido |
|---|---|---|
| E01 | Integraciones externas | Gmail, Outlook, Google Calendar, Microsoft Calendar y Slack |
| E02 | Aplicaciones móviles nativas | Aplicaciones independientes para Android y iOS |
| E03 | Carga masiva y captura por voz | Importaciones CSV, creación por voz y procesamiento masivo |
| E04 | Notificaciones externas | Push, correo electrónico y avisos del navegador |
| E05 | Personalización avanzada | Temas claro/oscuro, configuración individual de avisos y restablecimiento global |
| E06 | Exportación de datos | Descarga de tareas, proyectos y eventos |
| E07 | Analítica avanzada | Medición de tiempo real, estadísticas complejas y análisis semanal avanzado de carga |
| E08 | Gamificación avanzada | Niveles, rankings, tiendas de recompensas y catálogos extensos de insignias |
| E09 | Colaboración y equipos | Espacios compartidos, asignación de tareas y gestión de permisos entre usuarios |
| E10 | Automatización inteligente | IA que reorganiza tareas, modifica compromisos o decide sin confirmación |
| E11 | Gestión avanzada de proyectos | Dependencias, diagramas de Gantt, presupuestos y seguimiento de recursos |
| E12 | Mensajes motivacionales | Mensajes automáticos de felicitación y reconocimiento (pospuestos en F06-D04) |

---

## 7. Etapa 5 — Criterios de éxito (S01–S10)

**Aprobados explícitamente, sin modificaciones.**

| ID | Criterio | Descripción |
|---|---|---|
| S01 | Flujo completo de tareas | Crear, organizar, planificar y completar tareas sin depender de herramientas externas |
| S02 | Planificación funcional | Visualizar agenda, asignar bloques y detectar conflictos conforme a F02 |
| S03 | Visibilidad del día | Dashboard con pendientes, próximos compromisos, vencimientos y progreso |
| S04 | Organización personal | Gestionar áreas y proyectos con el progreso básico aprobado |
| S05 | Recordatorios internos | Avisos relevantes sin duplicaciones ni acumulación de avisos obsoletos |
| S06 | Motivación funcional | Metas diarias, puntos, insignias y rachas funcionando conforme a F06 |
| S07 | Persistencia y continuidad | Conservar tareas, planificación, preferencias y progreso entre sesiones |
| S08 | Uso cotidiano sencillo | Capturar una tarea rápidamente y consultar la planificación sin pasos innecesarios |
| S09 | Validación con usuarios reales | Prueba de uso de **al menos 7 días** con usuarios piloto |
| S10 | Criterios de aceptación | Cumplir los criterios de aceptación aprobados de F01–F07, sin defectos críticos abiertos |

### Definición de "MVP validado"

El MVP se considera funcionalmente validado cuando:

- Cumple los criterios de aceptación de F01–F07 sin defectos críticos abiertos.
- Permite gestionar tareas, proyectos, calendario, Dashboard, avisos y motivación de extremo a extremo.
- Conserva correctamente la información entre sesiones.
- Ofrece una experiencia sencilla de captura y planificación.
- Completa una **prueba piloto de al menos siete días con usuarios reales**, recopilando problemas y comentarios.

**Aprobar el Discovery no significa que el producto esté construido o validado.**

---

## 8. Cierre formal y reglas de la línea base

**15 de noviembre de 2026 — Discovery funcional v1.0 declarado CERRADO por el usuario.**

Texto de aprobación: *"APRUEBO explícitamente y declaro CERRADO el Discovery funcional v1.0 del MVP, incluyendo las cinco etapas, F01–F07, exclusiones E01–E12 y criterios de éxito S01–S10. Registra el cierre como línea base funcional. No iniciar arquitectura ni implementación hasta mi autorización."*

### Reglas vigentes desde el cierre

1. No se modifican decisiones aprobadas sin identificar y autorizar el cambio.
2. No se amplía el alcance del MVP sin una revisión explícita.
3. Cualquier cambio posterior se registra como **solicitud de cambio**, sin alterar silenciosamente la versión aprobada.
4. La arquitectura y las tecnologías **siguen sin definir**.
5. **No se inicia arquitectura ni implementación hasta que el usuario lo autorice.**

### Estado del proyecto

| Fase | Estado |
|---|---|
| 1. Discovery funcional | Completado |
| 2. Arquitectura y diseño técnico | Sin iniciar |
| 3. Desarrollo del MVP | Sin iniciar |
| 4. Pruebas y validación | Sin iniciar |

---

## 9. Registro de solicitudes de cambio y ajustes de alcance

| Código | Descripción | Afecta | Resultado |
|---|---|---|---|
| CR-F03-01 | Prioridad (Alta/Media/Baja) y favorito independiente para proyectos; los favoritos se anclan en el Dashboard incluso sin tareas pendientes | F03, F04 (excepción a F04-D08) | Aprobado en F03 v1.1 |
| CR-F03-02 | Orden de proyectos: favoritos en sección separada; por prioridad descendente y alfabético en empate | F03, F04 | Aprobado en F03 v1.1 |
| F03-D04 | Se retira la eliminación de áreas de la primera versión; áreas predefinidas (solo renombrar y cambiar color) | F03 | Aprobado (decisión del usuario) |
| F04-D25 | Panel preventivo simplificado; ajusta D05/D17 | F04 | Aprobado con F04 v1.16 |
| F04-D18 | Análisis avanzado de carga semanal pasa a la versión v2 | F04 | Pospuesto |
| F02-D40 | Keep Simple: pospone medición de tiempo real y cálculos derivados (D17, D19, D20, D28, D30, D36, D37) | F02 | Aprobado |
| OBS-F02-01 | Dos opciones al eliminar eventos recurrentes (esta ocurrencia o toda la serie) | F02 (CA15, CA27) | Resuelta y aprobada |

---

## 10. Puntos abiertos y observaciones

Estos puntos **no bloquean** el cierre del Discovery, pero conviene resolverlos antes o durante el diseño detallado.

1. **Recurrencias mensuales en días 29, 30 y 31.** Se propuso usar el último día disponible del mes; no se formalizó como decisión.
2. **Trazabilidad de subtareas completadas automáticamente (F01-RN-04).** Se recomendó distinguir finalizaciones automáticas de manuales internamente; no se formalizó.
3. **Interpretación horaria de fechas límite sin hora explícita (F05).** Quedó como detalle para la especificación posterior.
4. **Alcance del primer despliegue vs. alcance funcional (F04).** Se recomendó separar qué componentes del Dashboard salen en el primer despliegue; el usuario aprobó F04 completo (v1.16) sin esa revisión. Queda pendiente definir el orden de entrega (F02 ya prevé entrega incremental P0/P1).
5. **D14 de F02 y referencia a "F07".** La matriz habla de F07 como contrato futuro de eventos externos, pero F07 final es Configuración y las integraciones están excluidas (E01). Conviene actualizar esa referencia en una próxima revisión documental.
6. **Autenticación y seguridad.** F07 presupone sesión autenticada; los mecanismos se definirán en la etapa de arquitectura.
7. **Gestión documental.** Quedó pendiente decidir el protocolo de registro de decisiones (ver Apéndice B).

---

## 11. Siguientes etapas (sin iniciar)

Cuando el usuario lo autorice:

1. **Arquitectura y diseño técnico:** definición de arquitectura, tecnologías, autenticación/seguridad, persistencia, infraestructura y despliegue.
2. **Backlog y plan de entrega incremental** (P0 → P1; primer despliegue funcional pequeño, con mejoras posteriores).
3. **Desarrollo del MVP.**
4. **Pruebas y validación:** criterios de aceptación F01–F07 y prueba piloto de al menos 7 días (S09).

---

## 12. Notas de reconstrucción

Este documento se consolidó el 15–16 de noviembre de 2026 a partir del registro original de las sesiones de Discovery, dado que la documentación no se había formalizado fuera de dicho registro.

**Fuentes usadas:** todos los mensajes del usuario (decisiones y aprobaciones) y las versiones finales de cada especificación presentada por el asistente (F01, F02 RC2 con resolución de OBS-F02-01, F03 v1.0 y v1.1, F04 v1.16, F05, F06, F07, exclusiones, criterios de éxito y cierre).

**Lo que no se pudo recuperar con detalle:**
- Las reglas de negocio numeradas **RN-F03-01 a RN-F03-57** de F03 y las reglas **RN-F04-01 a RN-F04-41** de F04 no aparecen en el texto recuperable. Su contenido funcional está cubierto por las decisiones D01–D16 (F03) y D01–D25 (F04) y por los criterios de aceptación. Si se necesita el detalle numerado original, debe consultarse el registro original de las sesiones.
- Los 22 criterios de F04 y los 20+6 de F03 se transcriben tal como se presentaron; en F03 v1.0 los 20 criterios estaban agrupados por tema sin código individual, por lo que aquí se numeran 1–20.
- Las decisiones D01–D43 de F02 están completas en la matriz de trazabilidad, pero el texto íntegro de algunas rondas intermedias de opciones no se transcribió; sí se registraron las decisiones elegidas por el usuario.
- Las horas exactas de cada aprobación no se transcribieron.

**Observaciones del reconstructor (no son decisiones del usuario):** la nota sobre D14/F07 y el punto 5 de la sección 10 son señales de inconsistencia detectadas al consolidar, no acuerdos tomados durante las sesiones.

---

## Apéndice A — Contexto previo (Focus OS)

Antes del Discovery formal, el asistente recuperó decisiones del planteamiento original llamado **Focus OS** (hoy DITSO/RELAJAO). Se mencionan como contexto histórico, **sin que se hayan reconfirmado como parte del Discovery v1.0**:

- Usuario y Workspace personal, preparado para soportar múltiples usuarios en el futuro, sin colaboración en el MVP.
- Life Areas para organizar tareas por áreas de vida.
- Objetivos diarios y semanales vinculados al progreso.
- Reflexión diaria como parte del dashboard.
- Persistencia de datos y autenticación (aplicación real, no solo prototipo).
- Dedicación prevista de **6 horas semanales** y filosofía de arquitectura simple, modular y segura.

Propuesta inicial de visión (antes de las etapas formales): *"un sistema operativo personal que transforma tareas, objetivos y compromisos dispersos en una visión clara del día, ayudando a decidir qué hacer, mantener el enfoque y visualizar el progreso sin complicar la vida."*

---

## Apéndice B — Propuesta de gestión documental (no aprobada)

Tras el cierre, el usuario pidió alternativas para que lo planificado y decidido **se conserve fuera de las sesiones de trabajo**. El asistente propuso lo siguiente; **no se aprobó ni se ejecutó ninguna acción**, y queda pendiente la decisión del usuario.

| Alternativa | Cómo funciona | Limitación |
|---|---|---|
| A. Markdown + GitHub | Especificaciones y decisiones versionadas como `.md` | Requiere mantener los archivos al día |
| B. GitHub Issues + Markdown | Cada requisito o decisión con su Issue | Puede generar demasiados Issues |
| C. GitHub Wiki | Páginas vinculadas | Contenido separado del repositorio |
| D. Notion o similar | Base de conocimiento visual | Dos fuentes que pueden desincronizarse |
| E. Automatización asistida por IA | Un agente actualiza documentos tras aprobaciones | Requiere integración, permisos y validación |

**Recomendación del asistente:** combinar A + B (modelo *Docs as Code + Decision Log + Pull Requests*), nivel **asistido** (la IA prepara los cambios y el usuario aprueba el PR), con GitHub como fuente oficial de verdad.

Estructura sugerida:

```text
RELAJAO/
├── README.md
├── CHANGELOG.md
└── docs/
    ├── 00-project/        vision.md · roadmap.md · glossary.md
    ├── 01-discovery/      discovery-v1.0.md · scope.md
    ├── 02-requirements/   F01-tasks.md · F02-calendar.md · F03-projects.md
    │                      F04-dashboard.md · F05-notifications.md
    │                      F06-motivation.md · F07-settings.md
    ├── 03-decisions/      decision-log.md · DEC-001.md
    └── 04-planning/       milestones.md · backlog.md
```

Protocolo propuesto en cuatro pasos: **Discutir → Aprobar → Documentar → Versionar** (una decisión solo es oficial cuando está confirmada en el repositorio). Pregunta pendiente: ¿cada sesión termina con un resumen documental propuesto para aprobación, o solo se registran los hitos importantes? (El asistente sugirió la primera opción.)

---

## Apéndice C — Descripción sugerida para GitHub

> **RELAJAO — Plataforma de productividad personal para organizar tareas, proyectos y tiempo, con planificación inteligente, seguimiento del progreso y enfoque Keep Simple.**
