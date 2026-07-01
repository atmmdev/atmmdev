# InvestNews CMS

Enterprise WordPress platform for a news portal and editorial products, with Bedrock architecture, custom theme, and an ecosystem of financial, marketing, SEO, and proprietary API integrations.

## Context

| Field                | Value                       |
| -------------------- | --------------------------- |
| **Company / Client** | InvestNews                  |
| **Industry**         | Media / Fintech / Editorial |
| **Your role**        | Full-stack Engineer         |
| **Team size**        | 25 Contributors             |

## Stack

| Layer                     | Technologies                                                                                                           |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **Core CMS**              | WordPress 6.9 · Bedrock (Roots) · PHP 8.2 · Composer                                                                   |
| **Theme/Frontend**        | Custom investnews theme + amp-investnews theme · Gutenberg (29 ACF blocks) · Custom JS/CSS                             |
| **Custom Fields**         | Advanced Custom Fields Pro                                                                                             |
| **SEO & Content**         | Rank Math · Custom JSON-LD · Custom Open Graph                                                                         |
| **Integrations**          | JWT Auth (REST) · Mailchimp · Beehiiv · ActiveCampaign · Yahoo Finance (RapidAPI) · CoinMarketCap · Dow Jones/WSJ feed |
| **Media & Email**         | S3 Uploads · WP SES                                                                                                    |
| **Build/Assets**          | Node 20 · Custom build.js (autoprefixer + cssnano + terser + watch mode)                                               |
| **Infrastructure/Deploy** | Heroku CNB stack in AWS CodeBuild pipeline                                                                             |
| **Quality/Security**      | PHPCS · PHPUnit (security suite) · GitHub Actions · OWASP ZAP                                                          |

## Business problem

High-volume financial editorial portal with multiple content types, calculators, market integrations, lead capture, marketing automations, and mobile monetization (AMP) — all with editorial governance, technical SEO, and enterprise security.

## What I did

- Developed enterprise WordPress editorial platform with Bedrock, PHP 8.2, and a highly complex custom theme.
- Implemented content architecture with 11 CPTs, 29 custom Gutenberg/ACF blocks, and conversion-oriented landing pages.
- Built integrations with external APIs (Yahoo Finance, CoinMarketCap, Dow Jones/WSJ) and marketing automations (Mailchimp, Beehiiv, ActiveCampaign).
- Created secure APIs and endpoints (JWT, nonce, capability checks) with structured logging and production observability.
- Optimized performance with transient cache, custom minification pipeline (Node), S3 uploads, and quality pipeline with GitHub Actions + security tests.

## Architecture

- Bedrock structure with per-environment configuration (development/staging/production) and variables via `.env`.
- Modular code by domain in `functions/helpers/*` (core, seo, finance, forms, integrations, taxonomy, admin).
- Centralized access control with reusable middlewares:
  - `investnews_require_ajax_capability`
  - `investnews_require_rest_capability`
  - `investnews_require_admin_post_capability`
- Centralized logging (`investnews_log`) with PSR-3 levels, correlation id, and PII/secrets masking.
- WordPress dependency management via Composer (plugins, mu-plugins, patches with `cweagans/composer-patches`).
- Security suite covering XSS, SQLi, authentication/authorization, and nonce validation.

## Implemented features

- Advanced editorial portal: multiple templates, reusable components, and 29 custom Gutenberg/ACF blocks.
- Content modeling with 11 custom CPTs: stocks, cryptocurrencies, asset simulator, profiles, guides, infographics, sponsored, newsletter contact, wsj-codes, fixed income, lead_renda_extra.
- Financial calculators and simulators: AJAX + REST endpoints (`renda-fixa/v1`), PDF generation, and rate limiting.
- Financial market integrations: Yahoo/CoinMarketCap data ingestion and caching.
- Lead capture and automation: LP forms, deduplication, CSV export, segmentation, and triggers to Mailchimp/Beehiiv/ActiveCampaign.
- WSJ promotional flow: code distribution via taxonomy, validations, scheduled sending, and email automation.
- Protected proprietary API: custom REST prefix (`inv-api`) with JWT and endpoint for authorized bot content creation.
- Technical SEO and editorial governance: canonical, robots, OG image, schema, and taxonomy/redirect rules.
- AMP and monetization: dedicated AMP theme, Advanced Ads, and mobile-optimized behavior.
- Observability: structured JSON logs with per-request correlation and sensitive data sanitization.

## CV bullets

- Built enterprise WordPress editorial platform with Bedrock, PHP 8.2, and a highly complex custom theme for a high-volume financial portal.
- Implemented content architecture with 11 CPTs, 29 custom Gutenberg/ACF blocks, and a complete conversion-oriented landing page flow.
- Built integrations with external APIs (Yahoo Finance, CoinMarketCap, Dow Jones/WSJ) and marketing automations (Mailchimp, Beehiiv, ActiveCampaign).
- Created secure APIs and endpoints (JWT, nonce, capability checks) with structured logging and production observability.
- Optimized performance with transient cache, custom minification pipeline (Node), S3 uploads, and quality pipeline with GitHub Actions + security tests.
