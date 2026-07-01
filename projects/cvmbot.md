# CVMBot (InvestNews - Intern Plataforma)

Editorial automation platform for monitoring CVM Material Facts, AI-powered content generation, and assisted publishing, with a modular Python backend and React admin panel.

## Context

| Field                | Value                |
| -------------------- | -------------------- |
| **Company / Client** | InvestNews           |
| **Industry**         | Media / Fintech / AI |
| **Your role**        | Full-stack Engineer  |
| **Team size**        | 25 Contributors      |

## Stack

| Layer                | Technologies                                                                               |
| -------------------- | ------------------------------------------------------------------------------------------ |
| **Backend Core**     | Python 3.14 · FastAPI · Uvicorn · Pydantic Settings · Structlog                            |
| **Content Pipeline** | Selenium · PyMuPDF (fitz) · OpenAI (GPT-4o) · AWS Bedrock (Claude Sonnet)                  |
| **Data**             | PostgreSQL · psycopg2-binary                                                               |
| **Auth/Security**    | JWT (python-jose) · bcrypt · CORS Middleware · Audit logging                               |
| **Admin Frontend**   | React 19 · React Router 7 · Vite 7 · Tailwind CSS 4 · TanStack Query 5 · Axios · Zustand 5 |
| **UI/Productivity**  | Monaco Editor · React Diff Viewer                                                          |
| **Testing**          | Pytest (backend) · Vitest + Testing Library (frontend) · Playwright (E2E)                  |
| **Integrations**     | WordPress REST API · WhatsApp (Z-API) · Evolution API · Baileys Bridge (Node/Express)      |
| **Observability**    | Structlog + operational execution logs                                                     |

## Business problem

Automate the editorial cycle for CVM Material Facts: monitor regulatory publications, extract content from PDFs, generate news with AI, evaluate editorial quality, and publish to WordPress with operational notifications.

## What I did

- Developed Python platform for editorial automation with CVM → AI → publishing pipeline inside WordPress.
- Implemented pipeline with Selenium, PyMuPDF, GPT-4o, and quality evaluation via Claude (AWS Bedrock).
- Built admin API with FastAPI, JWT/bcrypt authentication, audit trail, and prompt governance (versioning, deploy, rollback).
- Integrated PostgreSQL, WordPress REST API, and WhatsApp channels (Z-API/Baileys bridge).
- Developed React admin panel (React 19, Vite, Tailwind, TanStack Query, Zustand) with unit and E2E tests (Vitest/Playwright).

## Architecture

- Modular architecture in the `cvmbot` package with separation by domain (core, scrapers, processors, ai, integrations, database, admin).
- Central orchestrator (`CVMBotOrchestrator`) coordinating: discovery → parsing → generation → evaluation → publishing → notification.
- Repository pattern for data access and services by responsibility.
- Layered admin backend (api, services, repositories, models, schemas, middleware).
- SPA frontend (Vite + React Router) for prompt operations, review, and feedback tracking.

## Implemented features

- Automatic CVM monitoring with Material Facts scraping (ENET portal).
- Download and text extraction from regulatory PDFs for processing.
- News generation with GPT-4o, including formatting and editorial fine-tuning.
- Editorial quality evaluation via Claude (Bedrock), with scoring.
- Publishing via WordPress REST API (with JWT authentication on WP).
- Operational notification via WhatsApp (Z-API and alternative Baileys bridge).
- Admin API with JWT authentication and session (login, refresh, logout, me, password change).
- Prompt management with versioning, rendering, restore, and deploy/rollback flow.
- Feedback module with statistics, trends, categorization, and analytical endpoints.
- Dataset resources and fine-tuning triggers exposed in the admin backend.
- Administrative action audit and event trail.
