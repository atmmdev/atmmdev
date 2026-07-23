# Soccer Analytics do ATM - [Repository](https://github.com/atmmdev/soccer.analytics)

Personal football intelligence / sports-betting BI platform in a pnpm monorepo: fixture and odds ingestion, probabilistic analysis engines (Poisson/EV), ticket building, bankroll management, Bet365 history import, and AI-assisted explanations — NestJS backend and Next.js dashboard.

## Context

| Field                | Value                                         |
| -------------------- | --------------------------------------------- |
| **Company / Client** | Personal project                              |
| **Industry**         | Sports Analytics / Football Intelligence / BI |
| **Your role**        | Solo Full-stack Engineer                      |
| **Team size**        | 1 (solo)                                      |

## Stack

| Layer                     | Technologies                                                                                          |
| ------------------------- | ----------------------------------------------------------------------------------------------------- |
| **Backend**               | NestJS 11 · TypeScript 5 · Prisma 6 · PostgreSQL 16 · Passport JWT · class-validator/transformer · Swagger |
| **Frontend**              | Next.js 15 (App Router) · React 19 · TypeScript · Tailwind 3 · Shadcn/Radix · TanStack Query v5 · Zustand · Axios · Recharts · next-themes · Sonner |
| **Authentication**        | JWT access + refresh token · Passport JWT Strategy · AuthGuard on dashboard                           |
| **Data & Integrations**   | API-Football (api-sports.io) · OpenAI (optional, gpt-4o-mini) · custom Bet365 PDF parser              |
| **Monorepo & DX**         | pnpm workspaces 9 · Node ≥20 · concurrently · bootstrap script (env + Docker + migrate + seed + dev)  |
| **Local Infra**           | Docker Compose (PostgreSQL 16 + Redis 7)                                                              |
| **Quality**               | ESLint · Jest/ts-jest (API) · Specification-Driven Development (`.ai/`)                               |

## Business problem

Build a personal football intelligence toolkit that answers “what do the data indicate?” — ingesting fixtures and odds, running probabilistic models, assembling tickets with bankroll discipline, and studying real betting history — without being a bookmaker.

## What I did

- Designed and built the full monorepo end-to-end: NestJS API, Next.js dashboard, Prisma schema, Docker Compose, and bootstrap DX (`pnpm start`).
- Implemented API-Football ingestion for fixtures, odds, statistics, players, and lineups, with daily boot sync and periodic refresh.
- Built probabilistic analysis engines (Poisson matrix, fair odds, EV, confidence) with BET/WATCH/SKIP recommendations and historical snapshots.
- Delivered ticket builder (combined odds, Kelly-like stake, correlation alerts) and bankroll periods with ROI/yield tracking.
- Developed a custom Bet365 PDF parser (~1.2k LOC) with preview/import APIs and study-ticket models for backtesting real history.
- Added optional OpenAI narrative explanations on top of deterministic engines, plus a Research Lab with simulation strategies.
- Applied Specification-Driven Development with PRD, architecture, engines, tasks, and roadmap under `.ai/`.

## Architecture

- Modular monorepo (`apps/api` + `apps/web`) with clear Separation of Concerns between domain engines and HTTP modules.
- Engine-oriented NestJS pattern: DataEngine → Statistics/Player → AnalysisEngine → Ticket/AI, with thin controllers and a service layer.
- Frontend as a thin client: no business rules in the UI; TanStack Query for server state and Zustand for auth/UI/ticket draft.
- Relational persistence in PostgreSQL via Prisma; Redis provisioned in Compose (cache/queues planned, not yet active in code).
- Specification-Driven Development with PRD, architecture docs, engine specs, tasks, and roadmap in `.ai/`, plus betting knowledge base in `docs/betting/`.

## Impact

- End-to-end personal platform covering ingest → analysis → tickets → bankroll → study history in a single operable stack.
- Automated local DX: one command bootstraps env, Docker, migrations, seed, API, and web.
- Documented REST API with Swagger Bearer auth and public health check.
- Reusable study pipeline from real Bet365 PDFs into structured tickets for performance analysis.

## Implemented features

**Authentication & Platform**

- Single admin login via environment credentials.
- JWT access (~15m) + refresh (~7d) with client-side renewal.
- Route protection with `JwtAuthGuard` (API) and `AuthGuard` (frontend).
- Public health check and Swagger docs at `/api/docs`.

**Match Center & Data Sync**

- Full Prisma domain: competitions, seasons, teams, players, matches, statistics, odds/history, predictions, and snapshots.
- API-Football integration for fixtures, odds, statistics, players, and lineups.
- Sync orchestration: daily boot, periodic fixture refresh, and full resync.
- Match list/detail UI and sync status screens.

**Analysis Engines**

- StatisticsEngine (form, H2H, matchup metrics).
- AnalysisEngine (Poisson matrix, fair odds, EV, confidence, BET/WATCH/SKIP).
- PlayerEngine for props when performance data is available.
- Analysis snapshots with post-match resolution and league ticket suggestions.
- Markets, Scanner, Analyzer, and History screens.

**Tickets & Bankroll**

- TicketEngine with combined odds, Kelly-like stake, and correlation alerts.
- Ticket CRUD with calculation and persistence.
- Bankroll periods, ledger entries, ticket/study-ticket links, place/settle, and ROI/yield summaries.
- UI at `/tickets` and `/bankroll`.

**Study / Bet365 History**

- Custom Bet365 PDF parser (~1.2k LOC) with preview/import via API.
- StudyTicket / StudyTicketLeg models and CLI import/export from real tickets.
- Web panel for study-history analysis.

**Research Lab & AI**

- SimulationEngine with strategy CRUD/run (preferential historical data; synthetic fallback when needed).
- AiEngine with template explanations and optional OpenAI enhancement.
- Research UI (“IA Trader”).

**Ops & Dashboard**

- Widgets for bankroll, today’s matches, suggested markets, EV+, and recommended ticket.
- Global search, alerts from positive snapshots, performance reports, and settings.
- Authenticated `(dashboard)` route group.
