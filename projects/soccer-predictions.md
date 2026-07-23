# Soccer Predictions - [See Online](https://soccer.atmm.dev)

Full-stack football pools (bolões) platform in a monorepo (Next.js + NestJS): multi-provider authentication, fixture sync via external API, configurable per-pool scoring engine, rankings, email notifications, PWA, and unified front+API deploy on Hostinger.

## Context

| Field                | Value                                    |
| -------------------- | ---------------------------------------- |
| **Company / Client** | Personal project                         |
| **Industry**         | Sports / Social Gaming / Football Pools  |
| **Your role**        | Solo Full-stack Engineer                 |
| **Team size**        | 1 (solo)                                 |

## Stack

| Layer                  | Technologies                                                                                          |
| ---------------------- | ----------------------------------------------------------------------------------------------------- |
| **Frontend**           | Next.js 16.2 · React 19.2 · TypeScript 5 · Tailwind 4 · Shadcn/UI (Radix) · React Hook Form 7 · Zod 4 · Recharts · next-themes · React Easy Crop · Lucide/React Icons |
| **Backend**            | NestJS 11 · TypeScript 5.7 · Prisma 7 · MySQL 8 (MariaDB adapter) · Passport JWT · Passport Google OAuth 2.0 · custom Instagram OAuth · bcryptjs · class-validator/transformer · Swagger |
| **Local Infra**        | Docker Compose · MySQL 8 · Redis 7 (provisioned) · Node.js 22                                         |
| **Integrations**       | football-data.org v4 · Resend (email) · Sharp (images)                                                |
| **Jobs / Async**       | `@nestjs/schedule` (cron: live sync, daily sync, reminders, ranking)                                  |
| **Quality**            | ESLint 9 · eslint-config-next · Prettier · Jest 30 · Supertest · React Compiler                       |
| **Deploy**             | Hostinger Node.js app · unified bootstrap (`/api` → internal Nest) · Prisma migrate deploy            |

## Business problem

Run football prediction pools with friends or communities: sync real fixtures and scores, accept predictions before kickoff, score participants with configurable rules, publish rankings, and notify users — as a production PWA with a single deployable process.

## What I did

- Designed and built the full monorepo end-to-end: NestJS API, Next.js App Router frontend, Prisma/MySQL schema, Docker Compose, and Hostinger production bootstrap.
- Implemented multi-provider auth (local JWT, Google OAuth, custom Instagram OAuth) with email verification, password reset/change, and RBAC (SUPER_ADMIN, ADMIN, PARTICIPANT).
- Integrated football-data.org for championships, teams, fixtures, scores, and crests, with scheduled live/morning/night sync jobs.
- Built a configurable per-pool scoring engine (exact score, winner, draw, player/hat-trick bonuses, cup-stage multipliers) with idempotent sync and achievements history.
- Delivered product modules: pools, predictions with cutoff, rankings, activity feed, statistics (Recharts), notifications, and daily prediction reminders via Resend.
- Shipped PWA (manifest, service worker, offline page), dark mode, responsive UI (desktop tables + mobile cards), and unified Hostinger deploy with `/api` proxy.

## Architecture

- Backend modular by domain (identity, sports, betting, health) with application (services/DTOs/utils) and infrastructure (HTTP, jobs, integrations) layers.
- Clean Architecture / DDD / SOLID on NestJS; shared modules for Prisma, mail, and auth helpers.
- Frontend Feature-First: `app` routes separated from features, components, lib, hooks, and schemas.
- Separation of Concerns: service layer on the backend; API services/mappers/hooks on the frontend.
- Relational persistence in MySQL via Prisma 7; scoring rules and breakdown stored as typed JSON.

## Impact

- Production app at [soccer.atmm.dev](https://soccer.atmm.dev) with unified Node process (Next public + Nest internal + `/api` proxy).
- Automated fixture lifecycle: live sync every 5 minutes, morning sync, and night sync with ranking emails.
- Role-aware product flow: PARTICIPANT signup; promotion to ADMIN when creating the first pool.
- Operational DX with Docker Compose (MySQL/Redis), seed SUPER_ADMIN, Swagger, and Prisma migrate deploy on Hostinger.

## Implemented features

**Authentication & Identity**

- Local login with JWT Bearer and frontend session cookies.
- Google OAuth (Passport) and Instagram OAuth (custom flow) with avatar import.
- Email verification, password reset/change, and resend verification via Resend.
- RBAC: SUPER_ADMIN, ADMIN, PARTICIPANT; Next middleware with role-based route control.
- Signup as PARTICIPANT; promotion to ADMIN on first pool creation.

**Sports / Catalog**

- Import and management of championships (league/cup), teams, and fixtures.
- football-data.org integration (fixtures, scores, crests) with in-memory client cache.
- Schedulers: live sync every 5 min, morning sync, night sync (with standings emails).
- Fixture status mapping and cup phases (group through final).

**Betting / Pools**

- Pool CRUD per championship with configurable JSON scoring (exact score, winner, draw, player/hat-trick bonuses, cup-stage multipliers).
- Participants with status (ACTIVE/INACTIVE/PENDING) and pool discovery.
- Predictions with pre-kickoff cutoff; hide others’ picks until deadline.
- Scoring engine with idempotent per-pool sync (concurrent sync dedupe) and points/achievements history.
- Rankings, activity feed, daily prediction reminders, and ranking-update notifications.

**Frontend (App Router)**

- Feature-first modules: dashboard, championships, pools, participants, matches, predictions, rankings, activity, statistics, notifications, profile (avatar crop), settings, help, admin.
- Route groups `(auth)` / `(protected)`, dedicated layouts, responsive UI.
- PWA with manifest, service worker, and offline page.
- Dark mode via next-themes; forms with React Hook Form + Zod.

**Platform & Deploy**

- Monorepo with root-orchestrated build (`apps/api` + `apps/web`).
- Single start process: Nest internal + Next on public port, `/api` proxy, and health-check.
- Docker Compose for MySQL/Redis in development; SUPER_ADMIN seed.
