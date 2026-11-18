# DEC-001 — Estilo arquitectónico y stack tecnológico

| Campo | Valor |
|---|---|
| Identificador | DEC-001 |
| Versión | 1.0 |
| Estado | **Aprobada** — 16-nov-2026 |
| Tipo | Registro de decisión arquitectónica (ADR) |
| Relación | Habilita [ARC-002 — Arquitectura técnica](./ARC-002-arquitectura-tecnica.md); complementa [ARC-001](./ARC-001-contexto-y-responsabilidades.md) (neutral por diseño) |
| Fuente funcional | [Discovery v1.0](../01-discovery/discovery-v1.0.md) |

---

## 1. Contexto y criterios de decisión

| # | Criterio | Implicación |
|---|---|---|
| C1 | **Mantenimiento y operación por un solo desarrollador** | Minimizar piezas desplegables y superficie operativa: una aplicación, una base de datos, un pipeline |
| C2 | **Reutilización de código hacia clientes móviles (React Native)** | El contrato, el cliente de API y la lógica de datos del frontend deben ser compartibles entre web y móvil |
| C3 | **Tecnologías estables y open source** | Versiones consolidadas, con mantenimiento activo y sin dependencia de servicios propietarios |

Restricciones funcionales heredadas de la línea base: aplicación adaptable a escritorio/tableta/móvil sin apps nativas en el MVP (E02), sin integraciones externas (E01), sin notificaciones externas (E04), un usuario por cuenta (E09), autenticación y persistencia reales (F07, S07).

---

## 2. Decisión

### 2.1 Estilo arquitectónico

**Monolito modular con Clean Architecture dentro de cada módulo.**

- **Una sola aplicación desplegable** (un contenedor), con **un módulo por agrupación funcional** del Discovery (F01–F07).
- Dentro de cada módulo, **cuatro capas** con regla de dependencia estricta hacia el dominio (detalle en ARC-002 §3).
- Comunicación entre módulos **solo** por contratos públicos o eventos de dominio; nunca acceso directo al dominio ajeno.
- Fronteras verificadas automáticamente en CI (detalle en ARC-002 §7).

### 2.2 Stack tecnológico (TypeScript de extremo a extremo)

| Pieza | Tecnología | Rol |
|---|---|---|
| Lenguaje | **TypeScript** (estricto) | Único lenguaje del servidor al cliente |
| Backend | **NestJS 11** sobre adaptador **Fastify** | Monolito modular: módulos, DI e inyección de contratos nativos |
| Frontend web (MVP) | **React 18 + Vite + TanStack Query** | SPA que consume la API REST |
| Móvil (post-MVP) | **Expo (React Native)** | Entra al monorepo reutilizando contratos, cliente API y hooks |
| Contrato | **Zod + OpenAPI** | Una fuente de verdad: valida en backend y tipa a todos los clientes |
| Base de datos | **PostgreSQL 16** | Un esquema (namespace) por módulo |
| ORM | **Prisma** | Migraciones versionadas y cliente tipado |
| Autenticación | **Argon2 + sesión con cookie HttpOnly** | Sin proveedor externo (E01); el mismo endpoint emitirá bearer token cuando llegue móvil |
| Monorepo | **pnpm workspaces + Turborepo** | Apps y paquetes compartidos con builds cacheados |
| Despliegue | **Docker (contenedor único) + GitHub Actions** → free tier (Render/Fly.io/Railway) | CI/CD en el repositorio; costo cero |

---

## 3. Alternativas consideradas y descartadas

| Alternativa | Composición | Por qué se descarta |
|---|---|---|
| **A** | ASP.NET Core (C#) + React + PostgreSQL | La reutilización hacia React Native queda limitada al contrato OpenAPI: backend y clientes no comparten código fuente (tipos, validaciones, lógica de datos). Incumple C2 |
| **B** | Go (chi + sqlc) + SvelteKit + PostgreSQL | SvelteKit no tiene camino maduro hacia móvil nativo. La variante Go + React fue finalista y se descarta por la misma razón que A: comparte solo el contrato, no código fuente de extremo a extremo (C2) |
| **Microservicios** (cualquier stack) | Servicios independientes por capacidad | Incumple C1: costo de despliegue, red y observabilidad desproporcionado; los requisitos del MVP (E01, E04, E09, carga baja) no justifican distribución |

---

## 4. Consecuencias

**Positivas**

1. Contratos Zod, cliente de API y hooks de datos compartidos entre web y móvil; un cambio de contrato rompe en compilación en todos los clientes (C2).
2. Un contenedor, una base de datos, un pipeline (C1).
3. Ruta de evolución definida: el primer módulo candidato a extraerse como servicio es Notificaciones (F05), porque solo consume eventos. Condición de extracción: necesidad real de push/correo o carga que lo justifique — hoy no existe.

**Negativas y mitigaciones**

1. El tipado de TypeScript se borra en runtime → validación en frontera con Zod en cada entrada de la API.
2. Ecosistema npm con dependencias numerosas → dependencias mínimas y fijadas, lockfile versionado, actualización deliberada.

---

## 5. Vigencia

Aprobada el 16-nov-2026 por el responsable del producto. Cualquier cambio posterior del estilo o del stack se registra como una nueva decisión (DEC-00X) que sustituye a esta; esta decisión no se edita en silencio.
