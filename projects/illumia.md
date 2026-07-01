# ILLUMIA Customer Care Web - [See Online](https://www.directvla.com/ar/home)

DirecTV - Argentine, Customer Care web platform built with Next.js 16, focused on performance, security, scalability, and user experience, with modules for authentication, retention, cancellation, and PQRS management.

## Context

| Field                | Value                   |
| -------------------- | ----------------------- |
| **Company / Client** | Illumia                 |
| **Industry**         | Telecom / Customer Care |
| **Your role**        | Frontend Engineer       |
| **Team size**        | 65 Contributors         |

## Stack

| Layer                       | Technologies                                                                    |
| --------------------------- | ------------------------------------------------------------------------------- |
| **Frontend**                | Next.js 16.0.1 (App Router) · React 19.2.0 · TypeScript 5+                      |
| **Styling**                 | Tailwind CSS 4.0 · Custom Design System with design tokens                      |
| **State (Server)**          | TanStack Query v5.90.10                                                         |
| **State (Client)**          | Zustand 5.0.8 · React Context API                                               |
| **Forms**                   | React Hook Form 7.66.1 · Zod 4.1.12 · Hookform Resolvers 5.2.2                  |
| **Testing**                 | Jest 29.7.0 · React Testing Library 16.3.0 · User Event 14.6.1 · ts-jest 29.2.5 |
| **Quality**                 | ESLint 9 · eslint-config-next 16.0.1 · TypeScript strict mode                   |
| **i18n**                    | Custom (ES, PT-BR, EN)                                                          |
| **Deploy & Infrastructure** | AWS Amplify · AWS CloudFront · GitHub Actions (proposed pipeline)               |

## Business problem

Centralize customer service in a modern web platform: integrated chat, service cancellation and reactivation, PQRS management, and analytics — with multi-environment support and a foundation for feature flags.

## What I did

- Developed the Customer Care web application with Next.js 16, React 19, and TypeScript 5+.
- Implemented Feature-First architecture and App Router with route groups, authentication middleware, and separation between domain and infrastructure layers.
- Built authentication flow with JWT, refresh token rotation, and route protection.
- Managed state with TanStack Query (server state) and Zustand (client state), with intelligent caching.
- Delivered critical modules (Chat, Baja Servicios, Reactivación, PQRS) integrated with BFF and multi-stage environment.
- Established quality standards with TypeScript strict mode, ESLint, Jest/RTL, and Conventional Commits.
- Deployed on AWS Amplify with CloudFront and prepared CI/CD with GitHub Actions.

## Architecture

- Feature-First Architecture by business domain.
- Separation of Concerns across routes, features, shared, stores, lib, and i18n.
- MVC adapted for React with isolated service layer.
- Next.js App Router with route groups for public and protected routes.
- React Server Components, Streaming SSR, dynamic routes, and authentication middleware.
- Path aliases, barrel exports, and custom hooks for standardization.
- Prepared for observability with DataDog RUM, GA4, CloudWatch, and error tracking.

## Implemented features

**Authentication & Session**

- JWT Bearer Token authentication.
- Refresh token rotation for automatic renewal.
- Route protection with middleware and session control.
- Security strategy with secure credentials and session handling.

**Business Modules**

- Illumia Chat integrated into the service flow.
- Baja Servicios for service cancellation.
- Reactivación for customer reactivation.
- PQRS for petitions, complaints, claims, and suggestions.
- Analytics for behavior tracking and metrics.

**Integrations & Platform**

- BFF (Backend for Frontend) integration.
- Multi-environment support (development, staging, and production).
- Foundation prepared for feature flags and gradual rollout.

**Performance & Scalability**

- Automatic code splitting and lazy loading.
- Intelligent caching with TanStack Query (staleTime and gcTime).
- Image optimization with custom loader.
- Asset prefix with CDN for static delivery.
- Optimized build with SWC.
