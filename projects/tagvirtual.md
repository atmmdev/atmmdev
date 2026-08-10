# TagVirtual

[See Online](https://tagvirtual.com.br/)

## Overview

SaaS platform for virtual toll tag management, built as a microservices architecture in a monorepo with independent services for core product and Pix payments.

## Context

| Field | Value |
| --- | --- |
| **Company / Client** | LW Brasil |
| **Industry** | Fintech / Mobility / Toll |
| **My role** | Full-stack Engineer |
| **Team size** | 10 contributors |
| **Employer mapping** | Document in master when linking to a specific employer engagement |

## Business Problem

End-to-end management of the virtual toll tag lifecycle: customers, vehicles, toll passages, digital wallet, Pix payments, and integrations with toll operators and external vehicle lookup APIs.

## My Role

Full-stack engineer responsible for backend services, frontend product surfaces, payments isolation, cloud integrations, and operational concerns (auth, audit, async processing, observability).

## Responsibilities

- Built the SaaS platform and an isolated Pix payments service (Itaú).
- Implemented granular RBAC, MFA, audit logs, and soft deletes.
- Integrated AWS (ECS, ECR, S3, SQS, Secrets Manager) with deployment via Azure Pipelines and Docker.
- Delivered async processing with SQS, real-time WebSockets (Socket.io), CRON jobs, and Elastic APM.
- Developed the Next.js frontend with React, shadcn/ui, Zustand, and XLSX/PDF report exports.

## Architecture

- Microservices in a monorepo with service isolation for payments.
- DDD-oriented separation per feature: `domain` / `infra` / `presentation`.
- Repository Pattern + NestJS Dependency Injection.
- Custom guards (`AuthGuard`, `PermissionGuard`, `AccessLevelGuard`) and decorators (`@CurrentUser`, `@RequirePermission`, `@AccessLevel`).
- Global error handling via interceptors/filters with APM integration.
- Validation with Zod (environment) and class-validator (DTOs).
- Standardized pagination with `ParseQueryPipe`.

## Technologies

| Layer | Technologies |
| --- | --- |
| **Backend** | NestJS 11 · TypeScript 5.7 · TypeORM · Fastify · MySQL |
| **Frontend** | Next.js 15 · React 19 · Tailwind CSS · shadcn/ui (Radix UI) · Zustand |
| **Payments** | Isolated NestJS service · Itaú Pix · AWS SQS |
| **Authentication** | JWT · Passport.js · Argon2 · MFA · RBAC |
| **Messaging / Real-time** | AWS SQS · Socket.io |
| **Storage** | AWS S3 (presigned URLs) |
| **Infrastructure** | Docker · AWS ECS/ECR · AWS Secrets Manager |
| **CI/CD** | Azure Pipelines |
| **Monitoring** | Elastic APM |

## Technical Challenges

- Isolating Pix payments as an independent service while keeping the product cohesive.
- Modeling granular permissions (roles + permissions + access levels) without overcomplicating the UI.
- Coordinating async wallet/payment flows with reliable webhook handling.
- Operating cloud-native deploy and secrets management in an existing AWS architecture.

## Technical Decisions

- Separate payments service to reduce blast radius and clarify payment domain boundaries.
- SQS for asynchronous work instead of coupling request/response to slow external payment steps.
- Socket.io for operational notifications that need near real-time feedback.
- Feature-level DDD layering to keep NestJS modules maintainable as the product grew.
- Azure Pipelines → ECS as the deployment path aligned with the existing platform.

## Results

- Delivered a production SaaS covering customer/vehicle lifecycle, digital wallet, Pix payments, reporting, and operator integrations.
- Established security baseline with RBAC, MFA, audit logs, and soft deletes.
- Enabled async and real-time operational flows (SQS + WebSockets) with APM visibility.

> No invented business KPIs. Use only outcomes that can be defended in interview from this project.

## Lessons Learned

- Payment domains benefit from isolation early, especially when webhooks and async settlement are involved.
- Granular RBAC needs product partnership; permission models can become UX debt if over-designed.
- Observability (APM + structured errors) is part of fullstack delivery, not an afterthought.

## Resume Relevance

| Track | Relevance | Why |
| --- | --- | --- |
| **Fullstack** | High | NestJS + Next.js + payments + AWS + auth end-to-end |
| **Frontend** | Medium | Strong Next/React product UI, but backend/payments are central |
| **AI** | Low | No LLM/AI product scope |
| **.NET** | Low | No C# / ASP.NET Core in this project |

### Suggested CV angles

- **Fullstack / Node+Next:** microservices monorepo, Pix service, SQS, RBAC/MFA, ECS.
- **Frontend:** Next.js admin/product UI, reports, real-time notifications.
- **Avoid:** Cloud Architect framing; describe AWS as application deployment within an established architecture.
