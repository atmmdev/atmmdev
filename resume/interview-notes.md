# Interview Notes

Answers must stay inside documented experience (`master.md`, `projects/`).  
If you cannot point to a project or employer, say so — do not invent.

---

## React

**Q: How do you structure a large React/Next app?**  
A: Feature-First by business domain (Illumia): routes, features, shared, stores, lib. Keep domain UI close to its services/hooks; share only true design-system primitives.

**Q: Server vs client state?**  
A: TanStack Query for server cache/sync; Zustand or Redux for client/session/UI. Illumia used Query + Zustand; Portal used Redux Toolkit/Saga for auth/session plus Query for remote data.

**Q: Performance wins you can defend?**  
A: IBM: 55% page-load reduction via React/Next optimization and architecture. Thera: 60% UI performance from React/TS modernization. BairesDev: 45% load-time improvement replacing jQuery with React/TS.

## Next.js

**Q: App Router experience?**  
A: Illumia on Next.js App Router with route groups, auth middleware, RSC/streaming SSR patterns, and protected/public separation.

**Q: Auth in Next.js?**  
A: Illumia: JWT + refresh rotation + middleware route protection. Afya: NextAuth + Logto/OIDC corporate SSO. Portal: SAML with server-side sessions and CSRF.

**Q: When SSR vs client rendering?**  
A: Prefer server rendering for protected shells and initial data boundaries; keep interactive care/ops widgets client-side with clear service layers (Illumia/Portal patterns).

## TypeScript

**Q: How strict do you go?**  
A: Illumia used TypeScript strict mode with ESLint and typed forms (Zod). Treat types as API contracts between UI, BFF, and domain modules — especially in enterprise refactors.

## Node.js / NestJS

**Q: NestJS module design?**  
A: TagVirtual/Portal: domain modules with layered boundaries (domain/infra/presentation or application/infra/repository). DI, guards, pipes, interceptors for cross-cutting auth/errors.

**Q: Async workloads?**  
A: TagVirtual: SQS consumers, CRON, webhooks for Pix/toll flows. Afya: Kafka + webhook fallback with idempotency for catalog sync.

**Q: Why isolate a service?**  
A: TagVirtual payments service isolated Pix domain to reduce blast radius and clarify payment boundaries inside a monorepo.

## Architecture

**Q: Monolith vs microservices?**  
A: Prefer modular monolith until a boundary is painful. Portal stayed modular NestJS; TagVirtual isolated payments when domain risk justified it. Afya’s ecosystem is distributed across marketplace core + integration APIs.

**Q: DDD / Clean Architecture in practice?**  
A: Use boundaries to protect business rules from providers/UI — not ceremony. Afya ports/adapters for finance providers; TagVirtual feature layering; avoid over-abstracting early.

## Microservices

**Q: Real microservice experience?**  
A: Practical: TagVirtual multi-service monorepo; Afya multi-repo distributed ecosystem; Globant contribution to microservices-oriented architectures. Do not claim platform-wide service-mesh ownership.

## APIs

**Q: REST vs GraphQL?**  
A: Most delivery is REST. GraphQL appears in IBM integration work and certifications — speak to client integration and data-fetching needs, not as GraphQL platform architect unless asked with evidence.

**Q: API security patterns?**  
A: JWT/refresh (Illumia), OIDC SSO (Afya), SAML sessions (Portal), WordPress capability-checked REST + JWT (InvestNews), RBAC/MFA/audit (TagVirtual).

## Testing

**Q: How do you test UI?**  
A: Jest + RTL on frontend engagements; Illumia established Jest/RTL standards. Portal/Afya show large automated suites (cite file/test counts, not invented coverage stories beyond documented 80% Portal backend gate).

**Q: Testing AI features?**  
A: CVMBot uses Pytest/Vitest/Playwright plus operational audit and quality scoring — emphasize pipeline reliability and review UX over model-accuracy research claims.

## AI

**Q: Are you an ML Engineer?**  
A: No. I build AI-powered applications: LLM APIs, prompt governance, document processing, and product integrations (CVMBot).

**Q: Walk through CVMBot.**  
A: Discover CVM facts → extract PDF text → generate with GPT-4o → score with Claude on Bedrock → publish via WordPress REST → notify via WhatsApp. Admin FastAPI + React UI for prompts (version/deploy/rollback) and audit.

**Q: Prompt engineering in production?**  
A: Treat prompts as operable artifacts: versioning, deploy, rollback, feedback stats — not one-off chat experiments.

## Cloud

**Q: Are you a Cloud/DevOps engineer?**  
A: No. I develop applications deployed on AWS/GCP within established architectures (ECS/S3/SQS, Amplify, Cloud Run, BigQuery, Pub/Sub) with CI/CD and containers.

**Q: AWS examples?**  
A: TagVirtual ECS/ECR/S3/SQS/Secrets; Illumia Amplify/CloudFront; Afya ECR + ArgoCD; master also lists S3/EC2/Lambda/RDS familiarity.

## C#

**Q: How strong is your C#?**  
A: Complementary backend skill (ASP.NET Core, Web APIs, EF, Dapper, LINQ, SQL Server). Primary production depth is React/Next/TypeScript and Node/Nest. Studying to strengthen React + .NET fullstack roles — do not oversell senior .NET ownership.

## UX/UI

**Q: How does design background help?**  
A: Career started in Web Design/UX-UI (2000–2005) and UI specialist work. Helps translate Design Systems and flows into maintainable React UI with product/design partners (Globant, Illumia, ATMM).

## Leadership

**Q: Leadership examples?**  
A: Stay honest: large-team contribution (Illumia ~65, Afya ~55), quality gates/standards (Portal tests/coverage, Illumia TS strict/ESLint), and technical delivery ownership on modules/platforms. Do not invent people-management claims unless documented later.

## Remote Work

**Q: Remote experience?**  
A: Long remote track record: IBM (Germany remote), BairesDev (USA remote), Thera, Globant (Canada remote), ATMM. Comfortable with async collaboration across time zones.

## Behavioral Questions

**Q: Tell me about yourself.**  
A: Started in design/UI → frontend engineering → frontend-focused fullstack. Today: React/Next/TS depth + Node/Nest delivery; enterprise modernization and AI-powered product features. Point to one recent metric (55% IBM or CVMBot) based on the role.

**Q: Biggest impact?**  
A: Pick by role: Frontend → 55%/60%/45% performance & modernization. Fullstack → TagVirtual/Afya/Portal systems. AI → CVMBot pipeline + prompt governance.

**Q: Conflict / disagreement?**  
A: Prefer architecture trade-off stories: modular monolith vs service isolation; SSO complexity; keeping humans in the loop for AI publishing. Focus on user/risk impact, not drama.

**Q: Weakness / gap?**  
A: Valid gaps: deep Kubernetes ops, ML model training, primary C# production ownership. Show learning plan without diluting core React/Next strength.

**Q: Why this role?**  
A: Map to one of: React/Next engineering, Node/Next fullstack, UI frontend, AI-powered software, or React + .NET collaboration — using the matching resume version.

---

## Quick evidence map

| Claim | Evidence |
| --- | --- |
| Frontend performance | IBM 55%, Thera 60%, BairesDev 45% |
| Delivery acceleration | BairesDev +56% component architecture |
| Tech debt | IBM −35% |
| API performance | Globant −40%, Thera API +40% efficiency |
| AI product work | CVMBot |
| Enterprise frontend architecture | Illumia |
| Fullstack SaaS | TagVirtual |
| Distributed systems | Afya Kafka/SSO/GitOps |
| GCP enterprise portal | Portal Florestal |
