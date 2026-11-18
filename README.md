# RELAJAO

Organiza tus responsabilidades, planifica el tiempo disponible y reconoce tus avances sin añadir más carga mental.

RELAJAO reúne tareas, proyectos y áreas de vida, un calendario con sugerencias que requieren tu confirmación y progreso con gamificación ligera. **El sistema recomienda; el usuario decide.** Durante el Discovery el proyecto se llamó DITSO.

## Estado del proyecto

**18 de noviembre de 2026 · Preparación de construcción.** Discovery, arquitectura, modelo de dominio e historias aprobados. El SPEC técnico está incorporado como documento de construcción; sus decisiones nuevas pendientes se identifican expresamente. Desarrollo, pruebas del producto y piloto todavía no han iniciado.

| Entregable | Estado |
|---|---|
| Discovery funcional v1.0 | Cerrado y congelado el 15-nov-2026 |
| Arquitectura y stack — ARC-002 / DEC-001 | Aprobados el 16-nov-2026 |
| Contexto y contenedores C4 — ARC-001 v1.1 | Aprobados; versionados en feature, commit `8b65917` |
| Modelo de dominio v0.1 | Aprobado; versionado en feature, commit `8b65917` |
| Ocho incrementos y 35 historias de usuario | Documentación aprobada el 18-nov-2026; historias pendientes de construcción |
| SPEC técnico de construcción v0.2 | Documento aprobado el 18-nov-2026; propuestas DTP y puntos abiertos pendientes de decisión |

La aprobación de documentos no significa que las historias estén implementadas ni resuelve por sí sola los puntos abiertos señalados. Las actualizaciones documentales locales más recientes están pendientes de commit; no se afirma integración en `main` sin comprobarla.

## Insumos para construir

| Necesitás conocer | Documento de referencia |
|---|---|
| Qué entrega construir y cómo aceptarla | [Incrementos, historias y criterios de aceptación](docs/03-planificacion/incrementos-historias.md) |
| Cómo construirla: módulos, datos, API, seguridad, interfaz y pruebas | [SPEC técnico](docs/06-construccion/SPEC-TECNICO.md) |
| Qué significan los conceptos y qué reglas deben preservarse | [Modelo de dominio](docs/04-arquitectura/domain-model.md) |
| Qué comportamiento funcional está aprobado | [SPEC funcional](docs/02-requisitos/SPEC.md) y [requisitos F01–F07](docs/README.md#requisitos-funcionales) |
| Qué arquitectura y tecnologías son vinculantes | [DEC-001](docs/04-arquitectura/DEC-001-stack-y-estilo.md) y [ARC-002](docs/04-arquitectura/ARC-002-arquitectura-tecnica.md) |
| Qué alcance quedó congelado y qué está excluido | [Discovery funcional v1.0](docs/01-discovery/discovery-v1.0.md) |

**Recorrido de construcción:** elegir historia → leer sus criterios y reglas originales → revisar su sección técnica y las decisiones que la afectan → resolver decisiones pendientes antes de la parte afectada → implementar y probar → demostrar el incremento → versionar y revisar mediante PR.

El SPEC técnico desarrolla la construcción; las historias ordenan el trabajo y describen el resultado para el usuario. Ninguno reemplaza los criterios originales del Discovery. Si existe contradicción, se registra y resuelve explícitamente antes de construir el comportamiento afectado.

## Entregas del MVP

| Incremento | Resultado para el usuario | Historias |
|---|---|---|
| I01 | Capturar y ejecutar pendientes | HU-01–07 |
| I02 | Organizar trabajo y rutinas | HU-08–13 |
| I03 | Construir una agenda realista | HU-14–17 |
| I04 | Ajustar planificación con ayuda | HU-18–22 |
| I05 | Decidir qué hacer hoy desde el Dashboard | HU-23–27 |
| I06 | Atender avisos internos relevantes | HU-28–30 |
| I07 | Reconocer progreso y constancia | HU-31–34 |
| I08 | Validar el MVP con usuarios durante al menos siete días | HU-35 |

Disponibilidad de referencia: **6 horas semanales**, martes, jueves y sábado, en sesiones de 2 horas. Las fechas de entrega quedan pendientes de estimar las historias; no hay un plazo final reconfirmado. El [backlog](docs/03-planificacion/incrementos-historias.md) contiene alcance, dependencias y aceptación de cada incremento.

## Arquitectura aprobada

Monolito modular con Clean Architecture dentro de cada módulo. La web se ejecuta en el navegador; un contenedor Docker sirve los archivos web y la API; PostgreSQL conserva los datos.

| Parte | Selección registrada en DEC-001 |
|---|---|
| Lenguaje | TypeScript estricto |
| API | NestJS 11 + Fastify |
| Web | React 18 + Vite + TanStack Query |
| Contratos | Zod + OpenAPI |
| Datos | PostgreSQL 16 + Prisma |
| Acceso | Argon2 y sesión con cookie HttpOnly |
| Repositorio y operación | pnpm workspaces, Turborepo, Docker y GitHub Actions |

Estas son las selecciones documentadas, no dependencias ya instaladas. Los detalles adicionales del SPEC marcados DTP siguen sujetos a decisión; no se cambia el stack por incorporar este documento.

## Estructura actual

```text
docs/
├── 01-discovery/       Línea base congelada del producto
├── 02-requisitos/      SPEC funcional y F01–F07
├── 03-planificacion/   Incrementos e historias de usuario
├── 04-arquitectura/    Decisiones, dominio y diagramas C4
├── 05-prototipo/       Prototipo de interfaz
└── 06-construccion/    SPEC técnico aprobado y guía UI
```

El código, las migraciones, los comandos de ejecución y el pipeline todavía no existen en este checkout. La estructura de código prevista está en [ARC-002](docs/04-arquitectura/ARC-002-arquitectura-tecnica.md#5-estructura-del-monorepo); se incorporará conforme se construyan las historias. Los comandos del SPEC son objetivos de implementación, no instrucciones de arranque disponibles hoy.

El [SPEC técnico aprobado](docs/06-construccion/SPEC-TECNICO.md) tiene una única ubicación en construcción. La [guía UI](docs/06-construccion/GUIA-CONSTRUCCION-UI.md) y el [prototipo](docs/05-prototipo/prototipo.html) son propuestas visuales; sus estados no cambian por reorganizar carpetas.

## Forma de trabajo

- Se trabaja siempre en `feature_initialDocs`. `main` conserva lo oficial y terminado.
- Cada historia se acepta mediante su comportamiento observable y los criterios originales aplicables; aprobar el backlog no marca historias como terminadas.
- Discovery v1.0 permanece congelado. Cambios funcionales o arquitectónicos requieren registro y aprobación explícitos.
- Las decisiones DTP se revisan en el [SPEC técnico, sección 17](docs/06-construccion/SPEC-TECNICO.md#17-decisiones-técnicas-propuestas-y-puntos-abiertos). Las dudas del dominio mantienen su trazabilidad.
- El MVP conserva F01–F07 y las exclusiones E01–E12. No incluye integraciones externas, aplicaciones nativas, colaboración, notificaciones externas ni automatización que decide sin confirmación.

[Índice completo de documentación](docs/README.md) · [Registro de cambios](CHANGELOG.md) · [Licencia MIT](LICENSE)
