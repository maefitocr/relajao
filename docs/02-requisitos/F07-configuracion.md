# F07 — Configuración y preferencias

| Campo | Valor |
|---|---|
| Estado | **Aprobado** |
| Versión | 1.0 |
| Aprobación | 15-nov-2026, dentro del [Discovery funcional v1.0](../01-discovery/discovery-v1.0.md) |
| Cambios posteriores | Referencias documentales actualizadas el 18-nov-2026; sin cambios funcionales |

## 1. Objetivo

Centralizar en una sección sencilla las preferencias ya aprobadas en otras funcionalidades (F02 y F06) y la gestión básica de perfil y sesión, sin introducir sistemas paralelos.

## 2. Capacidades

| ID | Capacidad | Decisión | Alcance |
|---|---|---|---|
| D01 | Perfil básico | Incluir | Consultar y editar el nombre visible |
| D02 | Zona horaria | Incluir | Consultar y modificar la zona horaria |
| D03 | Disponibilidad habitual | Incluir | Acceso a horarios, excepciones y descansos de F02 |
| D04 | Meta diaria | Incluir | Consultar, modificar o desactivar la meta de F06 |
| D05 | Apariencia (claro/oscuro) | **Pospuesto** (E05) | — |
| D06 | Preferencias de avisos | **Pospuesto** (E05) | — |
| D07 | Exportación de datos | **Pospuesto** (E06) | — |
| D08 | Gestión de cuenta | Incluir | Ver información básica de la cuenta y cerrar sesión |
| D09 | Restablecimiento de preferencias | **Pospuesto** (E05) | — |

## 3. Reglas de negocio

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

## 4. Criterios de aceptación (17)

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

## 5. Fuera de alcance

Apariencia claro/oscuro, preferencias individuales de avisos y restablecimiento global (E05) · exportación de datos (E06).

## 6. Puntos abiertos

1. **Autenticación y seguridad:** la sesión está prevista en [DEC-001](../04-arquitectura/DEC-001-stack-y-estilo.md) (Argon2 y cookie HttpOnly). El [SPEC técnico §17](../06-construccion/SPEC-TECNICO.md#17-decisiones-técnicas-propuestas-y-puntos-abiertos) conserva pendientes las políticas detalladas de acceso y sesión; no se deciden en este documento funcional.

## 7. Dependencias

- **F02:** disponibilidad, excepciones, descansos y zona horaria que esta sección expone.
- **F06:** meta diaria que esta sección configura.
