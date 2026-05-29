# Architecture Technique — ChartAPI

## Stack Technique Complète

### Composants Principaux
| Couche | Technologie | Justification | Coût |
|---|---|---|---|
| **API Gateway** | Cloudflare Workers | Edge computing, 0ms cold start, pricing free tiers généreux | \$0 (Free) |
| **Database** | Cloudflare D1 (SQLite) | Serverless SQL, scale to zero, intégration Workers native | \$0+ (pay-per-use) |
| **Cache** | Cloudflare KV | Cache distribué, lectures 5µs, TTL configurable | \$0 (Free: 100k reads/jour) |
| **Storage** | Cloudflare R2 | Stockage S3-compatible, pas de frais d'egress | \$0 (10GB Free) |
| **Auth/Billing** | Supabase | Auth + Stripe intégré, généreux free tier | \$0 (Free) |
| **Orchestration** | n8n (self-hosted) | Workflows, webhooks, alertes, 0 coût infra | \$0 |
| **Frontend** | Next.js + Tailwind | Dashboard, landing, docs, SSG/SSR | \$0 (Vercel Free) |
| **Scrapers** | Python + Playwright | Collecte données kworb.net | \$0 (GitHub Actions) |

### Coûts par Phase

| Phase | Période | Coût/mois | Scaling |
|---|---|---|---|
| **MVP** | Mois 1-3 | \$5.83 | Workers Free, D1 gratuit, KV gratuit, R2 gratuit |
| **Growth** | Mois 4-12 | \$127 | Workers Paid (\$5), D1 (\$20), KV (\$2), R2 (\$10), Supabase Pro (\$25), Domaine (\$10), Vercel Pro (\$20), n8n cloud (\$20), Monitoring (\$15) |
| **Scale** | An 2+ | \$295 | Workers Enterprise (\$50), D1 scale (\$50), KV (\$5), R2 (\$30), Supabase Team (\$60), Observabilité (\$50), Support (\$50) |

### Roadmap 6 Week-ends

| Weekend | Livrable | Technologies | Détail |
|---|---|---|---|
| **W1** | Scraper kworb.net + D1 | Python, Playwright, D1 | Script scraping + insertion D1 |
| **W2** | API REST + KV Cache | Cloudflare Workers, KV | Endpoints + caching |
| **W3** | Auth + Billing | Supabase, Stripe | Comptes + abonnements |
| **W4** | Dashboard MVP | Next.js, Tailwind, Recharts | UI analytics |
| **W5** | Alertes + Webhooks | n8n, Workers | Notifications temps réel |
| **W6** | Landing + Docs + Deploy | Next.js, Framer Motion | Site public + docs |
