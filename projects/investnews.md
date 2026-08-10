# InvestNews CMS

[See Online](https://investnews.com.br/)

## Overview

Enterprise WordPress editorial platform for a high-volume financial news portal, using Bedrock architecture, custom theme/blocks, financial and marketing integrations, and secured proprietary APIs.

## Context

| Field | Value |
| --- | --- |
| **Company / Client** | InvestNews |
| **Industry** | Media / Fintech / Editorial |
| **My role** | Full-stack Engineer |
| **Team size** | 25 contributors |
| **Employer mapping** | Document in master when linking to a specific employer engagement |
| **Related project** | CVMBot (AI publishing pipeline into this CMS) |

## Business Problem

Operate a high-volume financial editorial portal with multiple content types, calculators, market data integrations, lead capture, marketing automations, and mobile monetization (AMP) — under editorial governance, technical SEO, and enterprise security constraints.

## My Role

Full-stack engineer on the CMS platform: Bedrock/WordPress architecture, custom content model and Gutenberg blocks, secure REST APIs, third-party integrations, performance/security pipeline, and editorial tooling foundations used by downstream automation (CVMBot).

## Responsibilities

- Built the enterprise WordPress platform with Bedrock, PHP 8.2, and a complex custom theme.
- Implemented content architecture with 11 CPTs, 29 custom Gutenberg/ACF blocks, and conversion-oriented landing pages.
- Integrated external APIs (Yahoo Finance, CoinMarketCap, Dow Jones/WSJ) and marketing automations (Mailchimp, Beehiiv, ActiveCampaign).
- Created secure APIs/endpoints (JWT, nonce, capability checks) with structured logging and production observability.
- Optimized performance with transient cache, custom Node minification pipeline, S3 uploads, and quality/security checks via GitHub Actions.

## Architecture

- Bedrock structure with per-environment configuration and `.env`-driven settings.
- Modular domain helpers (`core`, `seo`, `finance`, `forms`, `integrations`, `taxonomy`, `admin`).
- Centralized access-control middlewares for AJAX, REST, and admin-post capabilities.
- Centralized logging with PSR-3 levels, correlation id, and PII/secrets masking.
- Composer-managed WordPress dependencies, plugins, mu-plugins, and patches.
- Security suite covering XSS, SQLi, authentication/authorization, and nonce validation.

## Technologies

| Layer | Technologies |
| --- | --- |
| **CMS Core** | WordPress 6.9 · Bedrock (Roots) · PHP 8.2 · Composer |
| **Theme / Frontend** | Custom themes · Gutenberg (29 ACF blocks) · Custom JS/CSS · AMP theme |
| **Fields / SEO** | ACF Pro · Rank Math · Custom JSON-LD / Open Graph |
| **Integrations** | JWT Auth · Mailchimp · Beehiiv · ActiveCampaign · Yahoo Finance · CoinMarketCap · Dow Jones/WSJ |
| **Media / Email** | S3 Uploads · WP SES |
| **Build** | Node 20 · custom build.js (autoprefixer, cssnano, terser) |
| **Deploy / Quality** | Heroku CNB on AWS CodeBuild · PHPCS · PHPUnit security suite · GitHub Actions · OWASP ZAP |

## Technical Challenges

- Modeling many editorial content types without turning the theme into an unmaintainable monolith.
- Securing custom REST/AJAX surfaces used by internal tools and bots.
- Keeping market-data and marketing integrations cacheable and operable under editorial traffic.
- Supporting AMP/monetization without fracturing the main theme architecture.

## Technical Decisions

- Bedrock for environment discipline and Composer-based dependency control.
- Domain-oriented helper modules instead of a single `functions.php` dump.
- Capability-checked proprietary API (`inv-api`) as the safe contract for automation (including CVMBot publishing).
- Structured logs with secret/PII masking as a production requirement, not optional debug output.

## Results

- Delivered an enterprise editorial CMS with 11 CPTs and 29 custom blocks.
- Established secure API contracts and a security-oriented quality pipeline.
- Created the content/publishing foundation later extended by CVMBot.

> No invented traffic or revenue KPIs. Keep claims to platform capability and delivery scope.

## Lessons Learned

- For editorial products, content modeling and permissioned APIs are the real scalability levers.
- CMS work is fullstack when custom APIs, integrations, and build/security pipelines are first-class.
- Clean API boundaries make AI automation (CVMBot) safer to attach later.

## Resume Relevance

| Track | Relevance | Why |
| --- | --- | --- |
| **Fullstack** | Medium | Strong PHP/WordPress + API/integrations; less modern Node/React primary stack |
| **Frontend** | Medium | Custom blocks/theme/AMP UI; useful for UI + content-product roles |
| **AI** | Low–Medium | Not an AI app itself; critical substrate for CVMBot |
| **.NET** | Low | No C# / ASP.NET Core in this project |

### Suggested CV angles

- **UI Frontend / content platforms:** Gutenberg blocks, editorial UX, landing flows, AMP.
- **Fullstack (broader):** secure REST, integrations, Bedrock enterprise CMS.
- **AI track companion:** pair with CVMBot as publishing destination / API contract.
