# Afya Marketplace Ecosystem

[See Online](https://institucional.afya.com.br/)

## Overview

Distributed marketplace ecosystem for physicians: e-commerce core, financial integrations, educational catalog sync, and distinct frontends for customer, admin, and seller journeys.

## Context

| Field | Value |
| --- | --- |
| **Company / Client** | Afya |
| **Industry** | Healthcare / Edtech / E-commerce |
| **My role** | Full-stack Engineer |
| **Team size** | 55 contributors |
| **Employer mapping** | Document in master when linking to a specific employer engagement |

## Business Problem

Build an internal physician marketplace covering e-commerce, financial products (insurance and pension), educational catalog synchronization, and separate customer/admin/seller journeys — across a distributed multi-repository architecture.

## My Role

Full-stack engineer contributing across marketplace core (Medusa/Mercur), Next.js/React frontends, NestJS integration APIs, SSO, financial provider workflows, and resilient async sync pipelines.

## Responsibilities

- Developed the distributed ecosystem: Medusa/Mercur e-commerce core, Next.js/React frontends, and NestJS APIs for financial integrations and catalog sync.
- Implemented end-to-end corporate SSO (Logto/OIDC) with NextAuth on the frontend and identity validation/sync on the backend.
- Built integrations with financial providers (Vinci and Forza), workflow engine, webhook adapters, and async processing with idempotency.
- Delivered educational catalog sync via Kafka + webhook fallback, with retries and operational audit.
- Supported CI/CD with GitHub Actions, Docker builds to AWS ECR, and GitOps deploy via ArgoCD/Helm.
- Implemented advanced checkout/cart behavior (promotions, price reconciliation, shared cart) and Segment analytics tracking.

## Architecture

- Domain-oriented modules by business context (product, workflow, webhook, providers, sync, audit, health).
- Ports/adapters and service layer to decouple business rules from external integrations.
- Idempotency and resilience patterns for webhook/Kafka/SSO paths.
- Polyglot persistence: PostgreSQL/Redis for transactional marketplace core; MongoDB for integration, workflow, and audit data.
- CI/CD with image builds to ECR and GitOps deployment via ArgoCD/Helm across environments.

## Technologies

| Layer | Technologies |
| --- | --- |
| **Marketplace Backend** | Medusa 2.x (Node.js/TypeScript) · Mercur · PostgreSQL · Redis |
| **Integration APIs** | NestJS 10 · TypeScript · MongoDB/Mongoose · Axios · Swagger |
| **Customer Frontend** | Next.js 15 · React 19 · TypeScript · Tailwind 4 · HeroUI · Framer Motion |
| **Operational Frontends** | Vite · React · TypeScript · TanStack Query/Table · React Hook Form |
| **Authentication** | Logto/OIDC · NextAuth v5 · JWT |
| **Payments & Finance** | Stripe Connect · Vinci · Forza |
| **Messaging** | Kafka (kafkajs) · Webhooks · Cron (`@nestjs/schedule`) |
| **Observability** | Winston · MongoDB audit logs |
| **Platform** | S3 · Resend · Algolia · Docker · AWS ECR · ArgoCD/Helm · GitHub Actions |

## Technical Challenges

- Coordinating identity across frontend session (NextAuth) and backend marketplace/integration services.
- Keeping financial provider workflows resilient under async webhooks and partial failures.
- Syncing educational catalog reliably with Kafka primary path and webhook fallback without duplicating business rules.
- Operating in a large multi-contributor, multi-repo ecosystem without breaking domain boundaries.

## Technical Decisions

- Reuse the same business rules for Kafka and webhook ingestion to avoid divergent catalog states.
- Idempotency keys and distributed locks (MongoDB) to prevent race conditions in jobs.
- Separate NestJS integration APIs from Medusa core to isolate financial/edu sync complexity.
- SSO as a cross-cutting identity flow rather than per-frontend ad hoc auth.

## Results

- Delivered a distributed marketplace covering catalog, checkout, financial products, and seller/admin operations.
- Established resilient sync and webhook processing with auditability.
- Automated test suite reported in the project: **390+ unit and E2E tests**.

> Preserve this test count only as quality evidence. Do not invent commercial KPIs for Afya.

## Lessons Learned

- In marketplace platforms, identity sync and idempotency matter as much as UI polish.
- GitOps (ArgoCD/Helm) helps multi-environment delivery when many services evolve in parallel.
- Frontend complexity grows quickly when customer, admin, and seller journeys share concepts but not the same app shell.

## Resume Relevance

| Track | Relevance | Why |
| --- | --- | --- |
| **Fullstack** | High | Medusa + NestJS + Next.js + Kafka + SSO + payments |
| **Frontend** | High | Customer and operational React/Next experiences, checkout, SSO UX |
| **AI** | Low | No LLM product scope |
| **.NET** | Low | No C# / ASP.NET Core in this project |

### Suggested CV angles

- **Fullstack / Node+Next:** distributed marketplace, NestJS integrations, Kafka, GitOps.
- **Frontend / React+Next:** catalog/checkout journeys, NextAuth SSO, TanStack Query operational UIs.
- **UI Frontend:** strong if emphasizing design system usage, journey UX, and conversion flows — keep claims scoped to implemented UI work.
