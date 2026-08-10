# CVMBot

## Overview

Editorial automation platform that monitors CVM Material Facts, generates AI-assisted news content, scores editorial quality, and supports assisted publishing into InvestNews — with a Python/FastAPI backend and React admin panel.

## Context

| Field | Value |
| --- | --- |
| **Company / Client** | InvestNews |
| **Industry** | Media / Fintech / AI-powered applications |
| **My role** | Full-stack Engineer |
| **Team size** | 25 contributors |
| **Related project** | InvestNews CMS (WordPress publishing target) |
| **Employer mapping** | Document in master when linking to a specific employer engagement |

## Business Problem

Automate the editorial cycle for CVM Material Facts: monitor regulatory publications, extract PDF content, generate news with LLMs, evaluate editorial quality, publish to WordPress, and notify operations — without removing human editorial control.

## My Role

Full-stack engineer for the AI-powered editorial pipeline and admin experience: orchestration, model integrations (OpenAI + AWS Bedrock), prompt governance, FastAPI admin API, WordPress/WhatsApp integrations, and React operations UI.

## Responsibilities

- Built the Python platform for CVM → AI → publishing automation into WordPress.
- Implemented pipeline stages with Selenium, PyMuPDF, GPT-4o, and Claude quality evaluation on AWS Bedrock.
- Developed FastAPI admin API with JWT/bcrypt auth, audit trail, and prompt governance (versioning, deploy, rollback).
- Integrated PostgreSQL, WordPress REST API, and WhatsApp channels (Z-API / Baileys bridge).
- Developed the React admin panel (React 19, Vite, Tailwind, TanStack Query, Zustand) with unit and E2E tests (Vitest/Playwright).

## Architecture

- Modular `cvmbot` package by domain: core, scrapers, processors, ai, integrations, database, admin.
- Central orchestrator (`CVMBotOrchestrator`): discovery → parsing → generation → evaluation → publishing → notification.
- Repository pattern and responsibility-oriented services.
- Layered admin backend: api, services, repositories, models, schemas, middleware.
- SPA frontend for prompt operations, review, diffs, and feedback tracking.

## Technologies

| Layer | Technologies |
| --- | --- |
| **Backend** | Python · FastAPI · Uvicorn · Pydantic Settings · Structlog |
| **AI / Content Pipeline** | Selenium · PyMuPDF · OpenAI GPT-4o · AWS Bedrock (Claude Sonnet) |
| **Data** | PostgreSQL · psycopg2 |
| **Auth / Security** | JWT · bcrypt · CORS · Audit logging |
| **Admin Frontend** | React 19 · React Router · Vite · Tailwind CSS · TanStack Query · Axios · Zustand |
| **Editor UX** | Monaco Editor · React Diff Viewer |
| **Testing** | Pytest · Vitest · Testing Library · Playwright |
| **Integrations** | WordPress REST API · WhatsApp (Z-API, Evolution API, Baileys bridge) |

## Technical Challenges

- Turning noisy regulatory PDFs into reliable editorial inputs.
- Keeping humans in control via prompt governance, review UX, and auditability.
- Separating generation (GPT-4o) from quality evaluation (Claude/Bedrock) without brittle coupling.
- Integrating publishing and notifications into an existing CMS/operations stack.

## Technical Decisions

- Orchestrated pipeline with explicit stages instead of a single opaque “AI job”.
- Prompt versioning with deploy/rollback to treat prompts as operable artifacts.
- Dual-model approach: generation vs quality scoring responsibilities.
- Admin SPA focused on operator workflows (review, diff, feedback), not a generic chatbot UI.
- WordPress REST as the publishing contract already secured by the CMS platform.

## Results

- Delivered an operable CVM → AI → publish workflow with admin controls and audit trail.
- Enabled prompt governance (version, deploy, rollback) for editorial iteration.
- Connected generation quality scoring, WordPress publishing, and WhatsApp operational notifications.

> No invented deflection, cost-per-token, or accuracy KPIs. Do not present this as Machine Learning research or model training specialization.

## Lessons Learned

- Production AI value comes from pipeline reliability, governance, and operator UX — not model name-dropping.
- Prompt versioning and audit trails are what make LLM features maintainable in editorial teams.
- Clear boundaries with the CMS API reduce risk when automation writes content into production.

## Resume Relevance

| Track | Relevance | Why |
| --- | --- | --- |
| **Fullstack** | Medium | Strong Python/React delivery; less Nest/Next primary brand |
| **Frontend** | Medium | Solid React admin UX; not the headline frontend case study |
| **AI** | High | Primary evidence for AI-powered applications / LLM integration |
| **.NET** | Low | No C# / ASP.NET Core in this project |

### Suggested CV angles

- **AI Engineering (application-focused):** GPT-4o, Bedrock/Claude, prompt governance, document processing, WordPress publishing automation.
- **Fullstack:** FastAPI + React admin + PostgreSQL + integrations.
- **Do not use titles:** Machine Learning Engineer, Data Scientist, AI Researcher.
- **Keyword honesty:** LLM integration, prompt engineering, AI automation, document processing — not RAG/LangChain/vector DB unless later documented.
