# Audit Kworb.net & Marché Music Data Analytics — Opportunité ChartAPI

> **Date :** 29 mai 2026  
> **Équipe :** Forge d'Opportunités (6 experts)  
> **Concept retenu :** ChartAPI — API-as-a-Service de music data  
> **Repo :** https://github.com/fokomaximejoel/chartapi-audit

---

## Résumé Exécutif

| Métrique | Valeur |
|---|---|
| **Plateformes auditées** | 6 (kworb.net, Luminate, Chartmetric, Chartmasters, Soundcharts, Viberate) |
| **Marché mondial estimé (2026)** | \$1.5B – \$2.5B |
| **Nouveaux morceaux/jour** | 99,000 (96.2% indépendants) |
| **Gap critique identifié** | Entre \$0 (kworb.net) et \$19.90/mois (Viberate) — personne ne sert les indés/micro-labels |
| **Opportunité clé** | Aucune API publique abordable n'existe |

---

## Marché & Contexte

### Le Paysage Music Data

- **\$1.5-2.5B** : Taille estimée du marché global music data analytics en 2026
- **96.2%** des uploads musicaux proviennent d'artistes indépendants
- **99,000** nouveaux morceaux publiés chaque jour
- **Gap critique** : les artistes indés et micro-labels n'ont aucune solution abordable entre le gratuit (kworb.net) et \$19.90/mois (Viberate)
- **Aucune API publique** n'existe à prix abordable pour intégrer les données musicales dans d'autres applications

### Les Plateformes Auditées

| Plateforme | Prix | Positionnement | Forces | Faiblesses |
|---|---|---|---|---|
| **kworb.net** | Gratuit | One-man-band data addictif | Gratuit, addictif, données brutes complètes | UI minimaliste, pas d'API, pas de support |
| **Luminate** | \$395/mois | Enterprise data leader | Données certifiées Billboard, panels consommateurs | Prix inaccessible, pas de self-service |
| **Chartmetric** | \$140/mois | Middle-market data & playlists | Data playlist forte, curation éditoriale | Pas de prédiction, UX perfectible |
| **Chartmasters** | Freemium | Data journalism & communauté | Communauté engagée, contenus longs riches | Pas de produit SaaS structuré |
| **Soundcharts** | \$129/mois | Spécialiste radio & monitoring | 2400 radios, tracking temps réel | Limité à la radio, prix élevé |
| **Viberate** | \$19.90/mois | Disrupteur low-cost | 11M artistes, 24000 radios, pricing attractif | Design basique, fonctionnalités limitées |

---

## Scoring des Plateformes Concurrentes

| Rang | Plateforme | Score | Catégorie |
|---|---|---|---|
| 1 | **Viberate** | **81/100** | Disrupteur low-cost |
| 2 | **Luminate** | **70/100** | Monstre enterprise |
| 3 | **Soundcharts** | **66/100** | Spécialiste radio |
| 4 | **Chartmetric** | **65/100** | Middle-market |
| 5 | **Chartmasters** | **51/100** | Data journalisme |
| 6 | **Kworb.net** | **50/100** | One-man-band |

---

## Les 7 Gaps du Marché

| # | Gap | Impact | Opportunité |
|---|---|---|---|
| 1 | **Aucune API publique abordable** | Critique | ChartAPI comble ce vide |
| 2 | **Pas de prédiction IA** (que du reporting) | Fort | SIGNAL/Auris — A&R Copilot prédictif |
| 3 | **Pas d'alertes personnalisées** | Moyen | Notifications temps réel |
| 4 | **Mobile-first inexistant** | Moyen | App native analytics |
| 5 | **Design UX médiocre** | Fort | Interface moderne requise |
| 6 | **Pas d'intégration no-code** | Moyen | Zapier/Make/Notion connect |
| 7 | **Données historiques limitées** | Fort | Archives profondes |

---

## Concepts Produits Évalués

### Concept 1 : ChartAPI (Kworb Pro API) — Le Twilio de la music data

**Positionnement :** API REST temps réel pour charts musicaux

**Données disponibles :**
- Charts iTunes (100+ pays)
- Charts Spotify (50+ pays)
- Charts YouTube Music
- Charts Shazam
- Données historiques archivées

**Pricing :**
| Plan | Requêtes/mois | Prix |
|---|---|---|
| Free | 10,000 | \$0 |
| Starter | 100,000 | \$9.99 |
| Pro | 1,000,000 | \$29 |
| Enterprise | Custom | Sur devis |

**MVP :** 10 jours solo maker  
**Coût infra lancement :** \$5.83/mois  
**Stack :** Cloudflare Workers + D1 + KV + R2

### Concept 2 : SIGNAL/Auris — A&R Copilot IA prédictif

**Scoring Forge : 85/100**

- Scoring de "breakout potential" par IA
- Alertes personnalisées
- Intégration Notion native
- Pricing : \$29 – \$199/mois

### Concept 3 : PUBLIK/ChartHub — Plateforme communautaire open data

- Crowdsourcing de données musicales
- Mini-jeux de prédiction
- API communautaire gratuite
- Pricing : Free + \$4.99/mois supporter

---

## Architecture Technique

### Stack Recommandée

| Composant | Technologie | Rôle |
|---|---|---|
| **API Gateway** | Cloudflare Workers | Edge computing, routage API |
| **Database** | Cloudflare D1 (SQLite) | Données structurées charts |
| **Cache** | Cloudflare KV | Cache rapide, rate limiting |
| **Storage** | Cloudflare R2 | Archives historiques, backups |
| **Auth & Billing** | Supabase | Utilisateurs, abonnements Stripe |
| **Orchestration** | n8n | Workflows, webhooks, alertes |
| **Frontend Dashboard** | Next.js | Interface utilisateur |
| **Scrapers** | Python + Playwright | Collecte données kworb.net |

### Coûts Infrastructure

| Phase | Coût/mois | Détails |
|---|---|---|
| **MVP** (Mois 1-3) | \$5.83/mois | Workers Free + D1 + KV gratuit |
| **Growth** (Mois 4-12) | \$127/mois | Workers Paid + D1 + R2 |
| **Scale** (An 2+) | \$295/mois | Workers Enterprise + scaling |

### Roadmap Technique (6 week-ends)

| Weekend | Livrable | Technos |
|---|---|---|
| **W1** | Scraper kworb.net + base D1 | Python, Playwright, D1 |
| **W2** | API REST endpoints + KV cache | Cloudflare Workers |
| **W3** | Auth + Stripe billing | Supabase, Stripe |
| **W4** | Dashboard Next.js basique | Next.js, Tailwind |
| **W5** | Alertes + webhooks + n8n | n8n, Workers |
| **W6** | Landing page + docs + déploiement | Next.js, Framer Motion |

---

## Projections Financières

### ChartAPI — Scénario Réaliste (P50)

| Année | Revenus | Clients payants | MRR moyen | Marge brute |
|---|---|---|---|---|
| **Année 1** | **\$13,680** | 76 | \$15/user | 88% |
| **Année 2** | **\$68,400** | 380 | \$15/user | 88% |
| **Année 3** | **\$342,000** | 1,900 | \$15/user | 88% |

### Métriques Clés

| Métrique | Valeur |
|---|---|
| **Seuil de rentabilité** | Mois 2 |
| **Marge brute** | 88% |
| **ROI à 36 mois** | **3,400%** |
| **Coût d'acquisition client (CAC)** | \$5 (via SEO/content) |
| **LTV estimée** | \$540 (36 mois x \$15) |
| **Ratio LTV/CAC** | 108:1 |

## Prompts Vibe Coding (5 prompts prêts à l'emploi)

### Prompt 1 : Scraper kworb.net (Python)
> "Create a Python web scraper using Playwright that extracts daily chart data from kworb.net for iTunes, Spotify, YouTube Music, and Shazam across 50+ countries. Store results in Cloudflare D1 via the Workers API. Handle rate limiting with random delays (2-5s), retry logic (3 attempts), and HTML parsing with BeautifulSoup. Output structured JSON with: artist_name, song_title, platform, country, rank, date, streams_plays. Log all errors to a file."

### Prompt 2 : API REST (Cloudflare Workers)
> "Build a Cloudflare Worker that serves as a REST API for music chart data stored in Cloudflare D1. Endpoints needed: GET /charts/:platform/:country (daily/weekly/monthly), GET /artists/:id (full profile), GET /search?q=:query. Use KV for caching (TTL: 5 min for charts, 1 hour for artist data). Include CORS headers, rate limiting (100 req/min for free tier), and API key authentication via request headers. Return JSON responses."

### Prompt 3 : Dashboard (Next.js)
> "Create a Next.js 14 dashboard with Tailwind CSS and shadcn/ui for ChartAPI. Pages: Landing page (hero, pricing, features), Dashboard (charts overview, search, saved queries), API Docs (interactive Swagger UI). Features: Real-time search with debounce, chart visualization with Recharts, dark/light mode, responsive mobile-first design. Include a mock API layer for demo mode."

### Prompt 4 : Landing Page
> "Build a modern landing page for ChartAPI using Next.js + Tailwind + Framer Motion. Sections: Hero (animated headline + CTA), Features grid (API, real-time, 50+ countries, affordable pricing), Pricing cards (Free \$0, Starter \$9.99, Pro \$29), Testimonials carousel, Stats counter (10k+ developers, 50+ countries, 99.9% uptime), FAQ accordion, Footer. Use gradient backgrounds, subtle animations, and a clean dark theme."

### Prompt 5 : Billing (Stripe + Supabase)
> "Create a Next.js API route for Stripe subscription management linked to Supabase auth. Handle: /api/checkout (create Stripe checkout session with price tiers), /api/webhook (Stripe webhook for subscription events: created, updated, canceled, past_due), /api/portal (Stripe customer portal). Sync Stripe customer IDs with Supabase user profiles. Use environment variables for Stripe keys."

---

## Références & Sources

| Source | Type | URL |
|---|---|---|
| kworb.net | Plateforme auditée | https://kworb.net |
| Luminate | Plateforme auditée | https://luminatedata.com |
| Chartmetric | Plateforme auditée | https://chartmetric.com |
| Chartmasters | Plateforme auditée | https://chartmasters.org |
| Soundcharts | Plateforme auditée | https://soundcharts.com |
| Viberate | Plateforme auditée | https://viberate.com |
| IFPI Global Music Report | Rapport industrie | https://ifpi.org |
| MIDiA Research | Data marché | https://midiaresearch.com |

---

## Structure du Repository

```
chartapi-audit/
├── README.md                 ← Ce fichier (audit complet)
├── docs/
│   ├── analyse-concurrentielle.md
│   ├── gaps-du-marche.md
│   ├── concepts-produits.md
│   ├── architecture-technique.md
│   └── projections-financieres.md
├── prompts/
│   ├── scraper-kworb.md
│   ├── api-rest-worker.md
│   ├── dashboard-nextjs.md
│   ├── landing-page.md
│   └── billing-stripe.md
└── artefacts/
    ├── blueprint-chartapi.html
    └── schema-architecture.md
```

---

*Audit réalisé le 29 mai 2026 par l'équipe Forge d'Opportunités : Scout de Tendances, Analyste Financier, Evaluateur Stratégique, Concepteur de Produits, Architecte Technique, Gardien des Connaissances*
