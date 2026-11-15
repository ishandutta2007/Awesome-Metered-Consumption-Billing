# Awesome Metered & Consumption Billing [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of top **Metered and Consumption Billing** platforms, usage-based pricing software, event rating engines, and open-source infrastructure for ingesting high-frequency usage telemetry, managing entitlements, and automating revenue operations.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [Sector Overview & Market Dynamics](#-sector-overview--market-dynamics)
- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
- [Open-Source Software](#-open-source-software)
- [Feature Comparison Matrix](#-feature-comparison-matrix)
- [Contributing](#-contributing)
- [License](#-license)

---

## 📈 Sector Overview & Market Dynamics

The global cloud and usage-based billing management market is estimated at **$12.7B to $14.2B** (with the broader recurring subscription billing sector accounting for an additional **$7.5B to $8.5B**), driven by rapid expansion in AI token monetization, API-first software, and consumption-driven SaaS models. The sector is **moderately fragmented yet experiencing aggressive consolidation**, where high-scale point solutions are steadily acquired by payment networks and CRM giants (e.g., Stripe acquiring Metronome for ~$1B, Adyen acquiring Orb for $335M, and Salesforce acquiring m3ter), while independent open-source engines lead the developer-native infrastructure layer.

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted usage-based and metered billing platforms sorted by company scale (valuation / annual revenue in descending order).

| Platform | Company Size (Valuation / Revenue) | Starting Pricing (Specific Tier) | Free Tier / Trial Limit | Key Focus & Rating Architecture |
|---|---|---|---|---|
| **[Chargebee](https://www.chargebee.com/)** | **$3.5B Valuation** (~$202M ARR) | **$599/mo** (Performance plan, billed annually up to $100K/mo MRR) | **Starter Plan: $0/mo** free for the first **$250,000 in cumulative lifetime billing** (0.75% overage fee thereafter; includes CPQ Lite for first 50 quotes) | Subscription management engine with metered billing add-ons, prepaid credits, and hybrid recurring/usage invoicing. |
| **[Zuora](https://www.zuora.com/)** | **$1.7B Valuation** (~$450M Revenue, acquired by Silver Lake) | **$450,000/yr** (Enterprise entry contract via direct sales or AWS Marketplace Private Offer) | **No permanent free tier**; structured trial sandboxes (typically 14 to 30 days) granted upon request through enterprise sales | Enterprise quote-to-cash platform with ASC 606/IFRS 15 revenue recognition and multi-entity billing automation. |
| **[Metronome](https://metronome.com/)** | **$1.0B Acquisition** (Acquired by Stripe in 2026) | **0.8% of billings processed + $0.04 per 1,000 ingested events** (Starter Tier) | **No fixed platform subscription fee** on Starter (pay-as-you-grow volume rate; custom developer sandbox credits available) | High-volume usage metering and real-time rating engine engineered for AI tokens, compute, and complex pricing logic. |
| **[Orb](https://www.withorb.com/)** | **$335M Acquisition** (Acquired by Adyen in 2026) | **~$700/mo** (Business tier minimum platform fee with volume overages) | **No permanent free tier**; 30-day guided evaluation trial with simulated event pipelines upon sales onboarding | Multi-dimensional usage pricing, transparent invoice line items, and real-time ledger sync. |
| **[Amberflo](https://www.amberflo.io/)** | **$50M–$100M Est. Valuation** (~$2M–$3.3M ARR, $20M VC funding) | **$99/mo** (Startup plan covering baseline event ingestion, overages at ~$0.01 per 1,000 events) | **Free Developer Tier: 1,000,000 meter events/month** free forever; or 30-day full-feature trial for Growth tier | Metering-first architecture providing event-level tracking (AI tokens, API calls, GPU seconds) and cost governance. |
| **[m3ter](https://www.m3ter.com/)** | **$31.5M Venture Funding** (Acquired by Salesforce in 2026) | **Custom platform fee** (Enterprise contracts typically start at $1,000+/mo based on bill calculation volume) | **No permanent free tier**; bespoke interactive proof-of-concept (PoC) sandbox available via sales consultation | Advanced rating and data-pipeline layer bridging raw usage telemetry with Salesforce, HubSpot, and NetSuite ERPs. |

---

## 🟩 Open-Source Software

Self-hosted, developer-first, and community-driven metered consumption billing platforms, sorted by GitHub star count (descending).

### 1. [Lago](https://github.com/getlago/lago) [![GitHub stars](https://img.shields.io/github/stars/getlago/lago?style=social&color=white)](https://github.com/getlago/lago/stargazers)
- **Stack:** Ruby on Rails / PostgreSQL / Redis / ClickHouse
- **License:** AGPL-3.0
- **Overview:** Lago is the most widely adopted open-source metering and usage-based billing platform. It handles high-frequency event ingestion, complex aggregation rules (SUM, COUNT, MAX, unique counts), hybrid subscription plans, prepaid credits, and automated invoice delivery via Stripe, Adyen, or GoCardless.
- **Best for:** Teams seeking a comprehensive open-source alternative to Stripe Billing with mature event deduplication, grace periods, and wallet drawdown.

### 2. [Flexprice](https://github.com/flexprice/flexprice) [![GitHub stars](https://img.shields.io/github/stars/flexprice/flexprice?style=social&color=white)](https://github.com/flexprice/flexprice/stargazers)
- **Stack:** Go / TypeScript / PostgreSQL / Docker
- **License:** AGPL-3.0
- **Overview:** Flexprice is an open-source usage-based pricing and billing system built specifically for modern SaaS and AI applications. It offers real-time usage metering, wallet credits and automated top-ups, feature entitlement gating, dynamic rate cards, and an MCP server for autonomous AI agent integration.
- **Best for:** Developers building AI-native tools and usage-tiered APIs who want modern Go-based services, rich SDKs (Python, Go, JS), and no-code UI dashboards.

### 3. [Kill Bill](https://github.com/killbill/killbill) [![GitHub stars](https://img.shields.io/github/stars/killbill/killbill?style=social&color=white)](https://github.com/killbill/killbill/stargazers)
- **Stack:** Java / MySQL / MariaDB / PostgreSQL
- **License:** Apache-2.0
- **Overview:** Kill Bill is an enterprise-grade, battle-tested open-source subscription billing and payments platform running in production since 2010. It supports tiered, volume, and usage billing per subscription via its core engine, with modular plugins for payment gateways, tax calculation, and currency conversion.
- **Best for:** Organizations needing an Apache-2.0 permissively licensed billing core with complete on-premise data control, customizable plugin architectures, and modular financial compliance.

### 4. [OpenMeter](https://github.com/openmeterio/openmeter) [![GitHub stars](https://img.shields.io/github/stars/openmeterio/openmeter?style=social&color=white)](https://github.com/openmeterio/openmeter/stargazers)
- **Stack:** Go / PostgreSQL / ClickHouse / Apache Kafka
- **License:** Apache-2.0
- **Overview:** OpenMeter is a cloud-native, high-throughput event metering engine purpose-built for AI tokens, APIs, and cloud infrastructure consumption. It ingests CloudEvents format streams at massive scale via Kafka and ClickHouse, providing sub-second entitlement checks, real-time meter balances, and automated invoice generation.
- **Best for:** AI agent workflows, LLM infrastructure, and API providers requiring real-time token tracking, sub-millisecond rate limits, and permissive Apache-2.0 licensing.

### 5. [Lotus](https://github.com/uselotus/lotus) [![GitHub stars](https://img.shields.io/github/stars/uselotus/lotus?style=social&color=white)](https://github.com/uselotus/lotus/stargazers)
- **Stack:** Python / Django / React / PostgreSQL / ClickHouse
- **License:** MIT
- **Overview:** Lotus is an open-source pricing and packaging infrastructure platform designed to make experimentations with usage-based billing frictionless. It tracks product telemetry, models complex pricing metrics, monitors customer spend caps, and syncs seamlessly with payment processors such as Stripe.
- **Best for:** Python and full-stack developers seeking an MIT-licensed, developer-friendly interface to quickly prototype usage-based plans without getting bogged down in complex billing code.

### 6. [Meteroid](https://github.com/meteroid-oss/meteroid) [![GitHub stars](https://img.shields.io/github/stars/meteroid-oss/meteroid?style=social&color=white)](https://github.com/meteroid-oss/meteroid/stargazers)
- **Stack:** Rust / PostgreSQL / Docker
- **License:** AGPL-3.0
- **Overview:** Meteroid is a high-performance open-source pricing and billing infrastructure tool engineered in Rust. It manages the entire lifecycle from raw event ingestion, deduplication, and billable metric calculation to cost limiting, plan grandfathering, invoice generation, and revenue analytics.
- **Best for:** Engineering teams prioritizing blazing-fast Rust execution, memory efficiency, and built-in pricing experiment workflows.

### 7. [Tier](https://github.com/tierrun/tier) [![GitHub stars](https://img.shields.io/github/stars/tierrun/tier?style=social&color=white)](https://github.com/tierrun/tier/stargazers)
- **Stack:** Go / Stripe API
- **License:** BSD-3-Clause
- **Overview:** Tier introduced "Pricing as Code" (PriceOps) for SaaS businesses. Using a declarative `pricing.json` file, developers define usage meters, tiered structures, and subscription entitlements, allowing Tier CLI to automatically sync products and prices directly with Stripe.
- **Best for:** Teams using Stripe who want git-versioned pricing definitions, test environment previews, and entitlement checks without manual dashboard operations.

### 8. [Portcall](https://github.com/useportcall/portcall) [![GitHub stars](https://img.shields.io/github/stars/useportcall/portcall?style=social&color=white)](https://github.com/useportcall/portcall/stargazers)
- **Stack:** Go / PostgreSQL / TypeScript / React / Keycloak
- **License:** Open Source (GitHub)
- **Overview:** Portcall is a developer-first platform combining metered billing with entitlement management, feature flags, and quota enforcement. Built with Go microservices, event-driven message queues, and a Vite/React administration portal.
- **Best for:** Early-stage SaaS builders wanting integrated feature flags, quota limits, and usage billing within a unified monorepo architecture.

---

## 📊 Feature Comparison Matrix

| Solution | Deployment | License / Model | Real-Time Metering | LLM Token Tracking | Prepaid Wallets | Invoicing & Tax | Primary Use Case |
|---|---|---|:---:|:---:|:---:|:---:|---|
| **Chargebee** | Hosted SaaS | Proprietary | ⚠️ Add-on | ⚠️ Via Events | ✅ | ✅ Full Suite | Hybrid subscription & usage billing |
| **Zuora** | Hosted SaaS | Proprietary | ✅ Enterprise | ⚠️ Via Events | ✅ | ✅ Full Suite | Enterprise monetization & ASC 606 |
| **Metronome** | Hosted SaaS | Proprietary | ✅ High-volume | ✅ First-class | ✅ | ✅ | AI token & high-frequency rating |
| **Orb** | Hosted SaaS | Proprietary | ✅ Multi-dim | ✅ First-class | ✅ | ✅ | Multi-dimensional developer pricing |
| **Amberflo** | Hosted SaaS | Proprietary | ✅ Event-first | ✅ First-class | ✅ | ✅ | Metering-first telemetry & cost tracking |
| **m3ter** | Hosted SaaS | Proprietary | ✅ Data Pipeline | ⚠️ Via Events | ✅ | ⚠️ Via ERP | CRM/ERP rating layer |
| **Lago** | Self-Hosted | AGPL-3.0 | ✅ Ingestion | ⚠️ Via Events | ✅ | ✅ | Open-source Stripe Billing alternative |
| **Flexprice** | Self-Hosted | AGPL-3.0 | ✅ Ingestion | ✅ First-class | ✅ | ✅ | AI agents & usage-based billing |
| **Kill Bill** | Self-Hosted | Apache-2.0 | ⚠️ Via Aviate | ❌ | ✅ | ✅ Full Suite | Enterprise open-source billing engine |
| **OpenMeter** | Self-Hosted | Apache-2.0 | ✅ Real-time | ✅ First-class | ✅ | ✅ | High-throughput AI/API event metering |
| **Lotus** | Self-Hosted | MIT | ✅ Telemetry | ⚠️ Via Events | ✅ | ⚠️ Via Stripe | Developer-friendly pricing experiments |
| **Meteroid** | Self-Hosted | AGPL-3.0 | ✅ Real-time | ⚠️ Via Events | ✅ | ✅ | Rust-native pricing & cost limiting |
| **Tier** | CLI / Self-Hosted | BSD-3-Clause | ⚠️ Via Stripe | ❌ | ❌ | ⚠️ Via Stripe | Pricing as Code for Stripe |
| **Portcall** | Self-Hosted | Open Source | ✅ Real-time | ❌ | ⚠️ | ⚠️ | Entitlements & metered quota limits |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source or commercial Metered / Consumption Billing solution that should be added or updated:

1. Fork this repository.
2. Create a descriptive branch: `git checkout -b add-tool-name`.
3. Add the project with details (stack, pricing/licensing, key differentiator, and star badge if OSS).
4. Open a clean pull request!

---

## 📄 License

This collection is released under [CC0 1.0 Universal (Public Domain)](LICENSE). Individual tools and software retain their respective proprietary or open-source licenses.

---

⭐ **If this repository helps you navigate usage-based billing infrastructure, please star it on GitHub!** ⭐
