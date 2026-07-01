# Afya Marketplace Ecosystem - [See Online](https://institucional.afya.com.br/)

Distributed marketplace ecosystem for physicians: e-commerce core, financial integrations, educational catalog sync, and frontends for customer, admin, and seller.

## Context

| Field                | Value                            |
| -------------------- | -------------------------------- |
| **Company / Client** | Afya                             |
| **Industry**         | Healthcare / Edtech / E-commerce |
| **Your role**        | Full-stack Engineer              |
| **Team size**        | 55 Contributors                  |

## Stack

| Layer                           | Technologies                                                             |
| ------------------------------- | ------------------------------------------------------------------------ |
| **Marketplace Backend**         | Medusa 2.x (Node.js/TypeScript) · Mercur modules · PostgreSQL · Redis    |
| **Integration APIs**            | NestJS 10 · TypeScript 5 · MongoDB/Mongoose · Axios · Swagger            |
| **Customer Frontend**           | Next.js 15 · React 19 · TypeScript · Tailwind 4 · HeroUI · Framer Motion |
| **Operational Frontends**       | Vite · React · TypeScript · TanStack Query/Table · React Hook Form       |
| **Authentication**              | SSO Logto/OIDC · NextAuth v5 beta · JWT (Nest/Medusa)                    |
| **Payments & Finance**          | Stripe Connect (marketplace) · Vinci and Forza providers                 |
| **Messaging & Async**           | Kafka (kafkajs) · Webhooks · Cron jobs (`@nestjs/schedule`)              |
| **Observability**               | Winston structured logging · audit logs in MongoDB                       |
| **Storage/Notification/Search** | S3 provider · Resend/local notifications · Algolia                       |
| **Infrastructure & Deploy**     | Docker · AWS ECR · ArgoCD + Helm · GitHub Actions                        |

## Business problem

Physician marketplace intern platform covering e-commerce, financial products (insurance and pension), educational catalog synchronization, and distinct journeys for customer, admin, and seller — all in a distributed architecture across multiple repositories.

## What I did

- Developed the distributed ecosystem: e-commerce core (Medusa/Mercur), Next.js/React frontend, and NestJS APIs for financial integrations and catalog.
- Implemented end-to-end corporate SSO (Logto/OIDC) with NextAuth on the frontend and identity validation/sync on the backend.
- Built integrations with financial providers (Vinci and Forza), workflow engine, webhooks with adapters, and async processing with idempotency.
- Delivered educational catalog sync via Kafka + webhook fallback, with event queues, retries, and operational audit.
- Deployed CI/CD with GitHub Actions, Docker builds to AWS ECR, and GitOps deployment via ArgoCD/Helm.
- Implemented advanced checkout and cart features (promotions, price reconciliation, shared cart) and analytics tracking with Segment.

## Architecture

- Domain-Driven Development oriented pattern with modules per business context (product, workflow, webhook, providers, sync, audit, health).
- Ports/adapters and service layer to decouple business rules from external integrations.
- Idempotency and resilience in critical integrations (webhook/Kafka/SSO), with standardized error handling.
- Polyglot persistence: PostgreSQL/Redis for transactional core and MongoDB for integration/workflow/audit.
- CI/CD pipeline with image builds to ECR and GitOps deployment via ArgoCD/Helm across multiple environments.

## Impact

- Robust automated test suite: 390+ unit and E2E tests reported in the project.

## Implemented features

**Marketplace Core**

- Multi-seller management with seller, reviews, commissions, payout, and payment split modules.
- Custom APIs for external orders and payment status capture/update.
- Backend SSO integration with token validation via userinfo, customer creation/sync, and login audit.
- File upload via S3 provider; Resend notifications; Algolia search.

**Marketplace Frontend**

- Full catalog and checkout journey with Medusa Store API integration.
- SSO with NextAuth + Logto, unified session, and token consumption for authenticated calls.
- Cart in Context API with persistence, shared cart support, and distinct product/service flows.
- Promotions/coupons with discount reconciliation and automatic/manual rules.
- Segment tracking (page, identify, track), analytics, and consent management.
- Insurance and pension modules with profile pages and purchase history.

**Financial API**

- Financial marketplace API with modular architecture and per-provider workflow.
- Vinci integrations (survey, funds, simulation, document upload, enrollment, certificates) and Forza (specialties, simulation, order).
- Unified webhooks with adapters, async processing, and status history for audit.
- Distributed lock in MongoDB to prevent race conditions in jobs.

**Educon API**

- Middleware between Educon seller and Medusa/Mercur marketplace for educational catalog sync.
- Hybrid Kafka + webhook fallback ingestion, reusing the same business rules.
- Catalog topic consumption with manual offset commit and idempotency via deterministic key.
- Product/plan/financial plan/discount sync orchestration with local persistence in MongoDB.
- Async processing via event queue (pending/processing/failed) with retries and operational observability.
