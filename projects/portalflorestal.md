# Portal Florestal - [See Online](https://portalflorestal.suzanonet.com.br/login)

Corporate forestry operations platform with a modular NestJS backend and a plugin-oriented Next.js frontend, covering authentication, planning, optimization, analytics, and full-stack observability on GCP.

## Context

| Field                | Value                                      |
| -------------------- | ------------------------------------------ |
| **Company / Client** | Suzano                                     |
| **Industry**         | Forestry / Agribusiness / Enterprise       |
| **Your role**        | Fullstack Engineer (frontend-leaning)      |
| **Team size**        | Enterprise team                            |

## Stack

| Layer                   | Technologies                                                                                      |
| ----------------------- | ------------------------------------------------------------------------------------------------- |
| **Backend**             | NestJS 11 · TypeScript 5.9 · Prisma 7.8 · PostgreSQL 18 · Passport SAML · class-validator · Zod · Swagger |
| **Frontend**            | Next.js 16 · React 19 · TypeScript · Tailwind CSS 4 · Styled Components · MUI · AG Grid            |
| **State & Data (FE)**   | Redux Toolkit · Redux Persist · Redux-Saga · TanStack Query · Axios                               |
| **Cloud & Integrations**| GCP Cloud Run · Cloud SQL (PostgreSQL) · GCS · BigQuery · Firestore · Pub/Sub · Secret Manager    |
| **Observability**       | OpenTelemetry (backend + frontend server-side) · Datadog Logs / RUM / APM                         |
| **Security**            | Helmet · Rate Limit · CSP / Permissions Policy · HttpOnly session cookie · CSRF                   |
| **CI/CD**               | Azure Pipelines · CodeQL · Dependency Scanning · JUnit / Cobertura (backend)                      |
| **Containerization**    | Docker multi-stage (backend and frontend)                                                         |

## Business problem

Unify forestry operational modules (planning, optimization, monitoring, and analytics) into a single corporate portal with SSO, role-based access, cloud-native integrations, and production-grade security and observability.

## What I did

- Led technical delivery across the Portal Florestal ecosystem: modular NestJS backend by domain and plugin-oriented Next.js frontend.
- Implemented corporate SAML authentication with server-side sessions, CSRF protection, and custom role/permission guards.
- Built cloud-native GCP integrations (Cloud Run, Cloud SQL, GCS, BigQuery, Firestore, Pub/Sub) with secrets managed in Secret Manager.
- Evolved end-to-end security and observability with Helmet, CSP, OpenTelemetry, and Datadog (APM, Logs, RUM).
- Structured quality governance with large-scale automated tests, 80% coverage thresholds, and risk-oriented PR validation gates.
- Delivered critical forestry optimization modules (MLPlan, Puzzle, MandaChuva, Explorer, C14, CEM, SFO, SIRA) with focus on scalability and maintainability.

## Architecture

- Backend modular monolith with clear domain boundaries and layered separation: application, infrastructure, repository, controllers/services/presentation.
- NestJS Dependency Injection with repository contracts via interface tokens.
- Global exception handling and interceptors for logging and error context; environment config validated with Zod.
- Frontend App Router with feature/plugin-oriented architecture and composed providers for global context.
- Hybrid frontend state: Redux for app/session persistence, Redux-Saga for auth side effects, React Query for remote data cache and sync.
- Observability as a cross-cutting concern: OpenTelemetry auto-instrumentation with OTLP export on the backend; Datadog RUM/Logs and configurable telemetry factory on the frontend.
- CI/CD via Azure Pipelines (develop / release / main) with Docker images to Cloud Run, Prisma migrations, and Cloud SQL Proxy.

## Impact

- Backend quality gate with explicit global coverage threshold of 80% (branches, functions, lines, statements).
- Large automated test base: 333 backend test files and 138 frontend test files.
- PR validation on backend with formatting, build, dependency audit, changed-file test existence checks, and change-focused test execution.
- Pipeline security with CodeQL and dependency scanning across both projects.

## Implemented features

**Platform & Auth**

- Pluginized platform for operational forestry modules: C14, CEM, Explorer, MandaChuva, MLPlan, Puzzle, SFO, SIRA.
- Corporate SAML authentication with server-side session and login / logout / CSRF flow.
- Access control with roles and permissions via custom guards.

**Operations & Optimization**

- Optimization and planning modules (MLPlan / Puzzle), including status webhooks and scheduled precipitation routines.
- File and document management with upload/download and signed GCS URLs.
- Analytical and operational integrations with BigQuery, Firestore, and Pub/Sub.
- Domain-based frontend routes, plugin control area, and AI-assisted optimization module (Azure OpenAI) for alert summarization.

**Security, Quality & Telemetry**

- Full-stack telemetry with log/trace correlation and browser experience monitoring.
- HTTP security bootstrap (Helmet, rate limiting, CSP/Permissions Policy).
- Backend PR quality gates and Husky commit hooks with automated test verification.
