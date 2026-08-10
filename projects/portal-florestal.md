# Portal Florestal

[See Online](https://portalflorestal.suzanonet.com.br/login)

## Overview

Corporate forestry operations platform with a modular NestJS backend and a plugin-oriented Next.js frontend, covering authentication, planning, optimization, analytics, and full-stack observability on GCP.

## Context

| Field | Value |
| --- | --- |
| **Company / Client** | Suzano |
| **Industry** | Forestry / Agribusiness / Enterprise |
| **My role** | Fullstack Engineer (frontend-leaning) |
| **Team size** | Enterprise team |
| **Employer mapping** | Document in master when linking to a specific employer engagement |

## Business Problem

Unify forestry operational modules (planning, optimization, monitoring, and analytics) into one corporate portal with SSO, role-based access, cloud-native integrations, and production-grade security/observability.

## My Role

Fullstack engineer (frontend-leaning) contributing across modular NestJS domain services and plugin-oriented Next.js operational tools, including SAML auth, GCP integrations, security hardening, observability, and quality gates.

## Responsibilities

- Delivered across the Portal Florestal ecosystem: domain-oriented NestJS backend and plugin-oriented Next.js frontend.
- Implemented corporate SAML authentication with server-side sessions, CSRF protection, and custom role/permission guards.
- Built cloud-native GCP integrations (Cloud Run, Cloud SQL, GCS, BigQuery, Firestore, Pub/Sub) with secrets in Secret Manager.
- Evolved security and observability with Helmet, CSP, OpenTelemetry, and Datadog (APM, Logs, RUM).
- Structured quality governance with large automated test bases, coverage thresholds, and PR validation gates.
- Delivered critical forestry modules (MLPlan, Puzzle, MandaChuva, Explorer, C14, CEM, SFO, SIRA) with maintainability focus.
- Supported an AI-assisted optimization/alert summarization module using Azure OpenAI (application feature, not ML platform work).

## Architecture

- Backend modular monolith with domain boundaries and layered separation (application, infrastructure, repository, presentation).
- NestJS DI with repository contracts via interface tokens.
- Global exception handling/interceptors; environment config validated with Zod.
- Frontend App Router with feature/plugin architecture and composed providers.
- Hybrid frontend state: Redux Toolkit/Persist + Redux-Saga for auth/session side effects; TanStack Query for remote data.
- Observability as cross-cutting concern: OpenTelemetry → OTLP on backend; Datadog RUM/Logs on frontend.
- CI/CD via Azure Pipelines to Cloud Run, with Prisma migrations and Cloud SQL Proxy.

## Technologies

| Layer | Technologies |
| --- | --- |
| **Backend** | NestJS 11 · TypeScript · Prisma · PostgreSQL · Passport SAML · class-validator · Zod · Swagger |
| **Frontend** | Next.js 16 · React 19 · TypeScript · Tailwind CSS · Styled Components · MUI · AG Grid |
| **State / Data (FE)** | Redux Toolkit · Redux Persist · Redux-Saga · TanStack Query · Axios |
| **Cloud** | GCP Cloud Run · Cloud SQL · GCS · BigQuery · Firestore · Pub/Sub · Secret Manager |
| **Observability** | OpenTelemetry · Datadog Logs / RUM / APM |
| **Security** | Helmet · Rate Limit · CSP · HttpOnly session · CSRF |
| **CI/CD** | Azure Pipelines · CodeQL · Dependency Scanning · Docker |
| **AI (feature)** | Azure OpenAI (alert summarization assistance) |

## Technical Challenges

- Unifying many operational tools under one portal without a rigid monolith frontend.
- Corporate SAML + server-side session security in a modern Next.js app.
- Cloud-native data paths (BigQuery/Firestore/Pub/Sub) with clear domain ownership in NestJS.
- Maintaining high automated-test discipline in an enterprise delivery process.

## Technical Decisions

- Plugin-oriented frontend so operational modules can evolve semi-independently.
- Modular NestJS backend (not premature microservices) with strict domain boundaries.
- Hybrid state model: Redux for session/app persistence, React Query for server cache.
- Treat observability and security headers as platform defaults, not optional add-ons.
- Keep Azure OpenAI usage scoped to assisted summarization — not positioned as core AI platform ownership.

## Results

- Backend quality gate with explicit **80%** coverage threshold (branches, functions, lines, statements).
- Large automated test base: **333** backend test files and **138** frontend test files.
- PR validation with formatting, build, dependency audit, changed-file test checks, and focused test execution.
- Pipeline security with CodeQL and dependency scanning on backend and frontend.

> Preserve these quality metrics. Do not invent forestry business KPIs.

## Lessons Learned

- Plugin frontends work well for enterprise ops suites when auth, design system, and telemetry stay centralized.
- SAML/session security decisions dominate perceived reliability in corporate portals.
- High coverage thresholds only help when PR gates enforce them on changed code paths.

## Resume Relevance

| Track | Relevance | Why |
| --- | --- | --- |
| **Fullstack** | High | NestJS + Next.js + auth + GCP + CI/CD end-to-end |
| **Frontend** | High | Plugin architecture, complex operational UI, App Router, enterprise state |
| **AI** | Low–Medium | Azure OpenAI summarization feature only; secondary to CVMBot |
| **.NET** | Low | No C# / ASP.NET Core in this project |

### Suggested CV angles

- **Node/Next Fullstack:** modular NestJS, plugin Next.js, SAML, GCP integrations, Datadog.
- **React/Next Engineering:** plugin architecture, AG Grid operational UIs, hybrid state.
- **AI track:** only as supporting evidence of AI-assisted product features; lead with CVMBot instead.
- **Cloud framing:** “applications deployed on GCP within established cloud architecture” — not Cloud Engineer.
