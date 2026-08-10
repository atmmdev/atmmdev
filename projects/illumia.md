# ILLUMIA Customer Care Web

[See Online](https://www.directvla.com/ar/home)

## Overview

Customer Care web platform for DirecTV Argentina, built with Next.js, focused on performance, security, scalable UX, and critical service modules (chat, cancellation, reactivation, PQRS).

## Context

| Field | Value |
| --- | --- |
| **Company / Client** | Illumia / DirecTV Argentina |
| **Industry** | Telecom / Customer Care |
| **My role** | Frontend Engineer |
| **Team size** | 65 contributors |
| **Employer mapping** | Document in master when linking to a specific employer engagement |

## Business Problem

Centralize customer service in a modern web platform: integrated chat, service cancellation and reactivation, PQRS management, and analytics — with multi-environment support and a foundation for feature flags.

## My Role

Frontend engineer owning Customer Care application architecture and delivery: App Router structure, authentication/session flows, feature modules, state strategy, quality standards, and AWS Amplify deployment path.

## Responsibilities

- Developed the Customer Care web application with Next.js, React, and TypeScript.
- Implemented Feature-First architecture and App Router with route groups, auth middleware, and domain/infrastructure separation.
- Built JWT authentication with refresh token rotation and route protection.
- Managed server/client state with TanStack Query and Zustand, including caching strategy.
- Delivered critical modules (Chat, Baja Servicios, Reactivación, PQRS) integrated with a BFF.
- Established quality standards with TypeScript strict mode, ESLint, Jest/RTL, and Conventional Commits.
- Deployed on AWS Amplify with CloudFront and prepared CI/CD with GitHub Actions.

## Architecture

- Feature-First architecture by business domain.
- Separation across routes, features, shared, stores, lib, and i18n.
- MVC adapted for React with an isolated service layer.
- Next.js App Router with public/protected route groups.
- React Server Components, Streaming SSR, dynamic routes, and authentication middleware.
- Path aliases, barrel exports, and custom hooks for consistency.
- Observability foundation prepared for Datadog RUM, GA4, CloudWatch, and error tracking.

## Technologies

| Layer | Technologies |
| --- | --- |
| **Frontend** | Next.js 16 (App Router) · React 19 · TypeScript 5+ |
| **Styling** | Tailwind CSS 4 · Custom Design System / design tokens |
| **State** | TanStack Query v5 · Zustand · React Context API |
| **Forms** | React Hook Form · Zod · Hookform Resolvers |
| **Testing** | Jest · React Testing Library · User Event · ts-jest |
| **Quality** | ESLint · TypeScript strict mode |
| **i18n** | Custom (ES, PT-BR, EN) |
| **Deploy** | AWS Amplify · AWS CloudFront · GitHub Actions |

## Technical Challenges

- Protecting authenticated customer-care flows with reliable refresh-token rotation.
- Structuring a large feature set (chat, retention, cancellation, PQRS) without a monolithic UI layer.
- Balancing server state caching with sensitive customer operations.
- Delivering in a large enterprise team with multi-environment promotion needs.

## Technical Decisions

- Feature-First over page-centric structure to keep business domains cohesive.
- TanStack Query for server state; Zustand for client/UI state — avoid overloading Context.
- Middleware-based route protection aligned with App Router conventions.
- Amplify/CloudFront deployment within the existing AWS application hosting model.

## Results

- Delivered critical Customer Care modules integrated with BFF and multi-stage environments.
- Established a scalable frontend architecture (Feature-First + App Router) suitable for enterprise growth.
- Hardened auth/session handling with JWT refresh rotation and protected routes.

> No invented performance or conversion KPIs for Illumia. Prefer architecture and delivery outcomes unless a metric is later documented in master.

## Lessons Learned

- In customer-care products, auth/session edge cases are product risks, not just security chores.
- Feature-First pays off when multiple domains share design system primitives but diverge in workflows.
- BFF integration simplifies frontend contracts when backend landscapes are heterogeneous.

## Resume Relevance

| Track | Relevance | Why |
| --- | --- | --- |
| **Fullstack** | Medium | Frontend-heavy with BFF integration; limited backend ownership |
| **Frontend** | High | Flagship Next.js/React architecture, Design System, auth UX, critical modules |
| **AI** | Low | No LLM product scope |
| **.NET** | Low | No C# / ASP.NET Core in this project |

### Suggested CV angles

- **React/Next Engineering:** App Router, RSC/SSR, Feature-First, Design System, TanStack Query.
- **UI Frontend Developer:** design tokens, complex service workflows, i18n, accessible interaction patterns (only claim what was implemented).
- **Fullstack:** mention BFF integration and auth flows as complementary backend collaboration.
