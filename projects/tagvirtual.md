# TagVirtual - [See Online](https://tagvirtual.com.br/)

SaaS platform for virtual toll tag management with a microservices architecture in a monorepo with 3 independent services.

## Context

| Field                | Value                     |
| -------------------- | ------------------------- |
| **Company / Client** | LW Brasil                 |
| **Industry**         | Fintech / Mobility / Toll |
| **Your role**        | Full-stack Engineer       |
| **Team size**        | 10 Contributors           |

## Stack

| Layer              | Technologies                                                          |
| ------------------ | --------------------------------------------------------------------- |
| **Backend**        | NestJS 11 · TypeScript 5.7 · TypeORM · Fastify · MySQL                |
| **Frontend**       | Next.js 15 · React 19 · Tailwind CSS · shadcn/ui (Radix UI) · Zustand |
| **Payments**       | Isolated NestJS service · Itaú Pix · AWS SQS (consumer)               |
| **Authentication** | JWT · Passport.js · Argon2                                            |
| **Messaging**      | AWS SQS (async queues)                                                |
| **Storage**        | AWS S3 (presigned URLs)                                               |
| **Infrastructure** | Docker · AWS ECS/ECR · AWS Secrets Manager                            |
| **CI/CD**          | Azure Pipelines (6 pipelines) → AWS                                   |
| **Monitoring**     | Elastic APM                                                           |
| **Real-time**      | Socket.io (WebSockets)                                                |

## Business problem

End-to-end management of the virtual toll tag lifecycle: customers, vehicles, toll passages, digital wallet, Pix payments, and integrations with toll operators and external vehicle lookup APIs.

## What I did

- Full-stack development of the SaaS platform and an isolated Pix payments service (Itaú).
- Implementation of granular RBAC authentication, MFA, audit logs, and soft deletes.
- Integration with AWS (ECS, ECR, S3, SQS, Secrets Manager) and deployment via Azure Pipelines.
- Async processing with SQS, real-time WebSockets, CRON jobs, and observability with Elastic APM.
- Frontend with Next.js, React, shadcn/ui, Zustand, and XLSX/PDF report exports.

## Architecture

- DDD with `domain` / `infra` / `presentation` layer separation per feature.
- Repository Pattern + Dependency Injection (NestJS DI container).
- Custom guards: `AuthGuard`, `PermissionGuard`, `AccessLevelGuard`.
- Custom decorators: `@CurrentUser`, `@RequirePermission`, `@AccessLevel`.
- Global error handling: interceptors + filters with APM integration.
- Standardized pagination with `ParseQueryPipe`.
- Validation: Zod (env vars) + class-validator (DTOs).

## Implemented features

- **Authentication & Authorization:** Granular RBAC (roles + permissions), MFA, JWT refresh token, audit logs.
- **Customer/Vehicle Management:** CRUD with soft delete, toll plaza passage history.
- **Digital Wallet:** Balance, transactions, Pix payment gateway integration (Itaú).
- **Vehicle Lookup:** Integration with external APIs (Consulta Fácil, Movvia) with caching.
- **Reports & Finance:** XLSX/PDF export, dashboard with Recharts.
- **Lead Management:** Bulk upload via S3, capture and qualification.
- **Notifications:** Real-time system via Socket.io + persisted notifications.
- **Webhooks:** Callbacks from toll operators and Pix gateway.
- **CRON Jobs:** Scheduled async processing via `@nestjs/schedule`.
