# Awesome-Metered-Consumption-Billing

# Awesome Metered & Consumption Billing

> A curated list of top Metered and Consumption Billing platforms — both SaaS/Hosted commercial solutions and open-source alternatives for ingesting usage events, applying pricing, and generating invoices based on actual consumption.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [Metronome](#metronome)
  - [Orb](#orb)
  - [Chargebee Metered Billing](#chargebee-metered-billing)
  - [m3ter](#m3ter)
  - [Amberflo](#amberflo)
  - [Zuora Metering](#zuora-metering)
- [Open-Source Software](#-open-source-software)
  - [OpenMeter](#openmeter)
  - [Lago](#lago)
  - [Flexprice](#flexprice)
  - [Kill Bill (Aviate Metering)](#kill-bill-aviate-metering)
  - [Portcall](#portcall)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Metered and Consumption Billing platforms. These are not open-source but are included as reference points for feature comparison.

### Metronome
**Type:** High-volume usage metering and rating engine
Metronome was a leading independent usage-based billing platform before being acquired by Stripe. It specializes in high-volume event rating and complex pricing logic, turning raw usage into billable line items. The platform supports a wide range of aggregation types and dimensional pricing (group keys) for differentiating rates by model, region, or instance type.

### Orb
**Type:** Multi-dimensional pricing and invoice detail
Orb was known for compelling multi-dimensional pricing and detailed invoice line items before being acquired by Adyen. It supports flexible pricing models and provides clear visibility into how usage translates to charges. The acquisition introduces uncertainty about its long-term independence as a neutral metering layer.

### Chargebee Metered Billing
**Type:** Usage billing within subscription management
Chargebee provides metered billing as part of its broader subscription management platform, supporting hybrid models that blend base subscriptions with usage-based charges, credits, and overages on a single invoice. It is strongest when subscription logic is the core and usage layers on top, rather than being usage-first architecture.

### m3ter
**Type:** Metering and rating for Salesforce/ERP stacks
m3ter specializes in the middle layer between raw usage and downstream systems — normalizing usage, applying rates, and handing clean data to CRM and ERP. It was acquired by Salesforce, with plans to integrate its high-volume metering into Agentforce Revenue Management.

### Amberflo
**Type:** High-frequency event metering with cost governance
Amberflo is the notable corporately independent commercial vendor remaining after the 2026 acquisition wave. It is strongest when accurate event-level metering is the first problem — metering tokens, API calls, GPU seconds, and custom events, then applying pricing and generating invoices. The architecture is metering-first, with customer-level cost visibility alongside billing.

### Zuora Metering
**Type:** Enterprise monetization with usage rating
Zuora provides usage rating and metering as part of its enterprise monetization platform, with deep revenue recognition (ASC 606/IFRS 15) capabilities. It is built for large organizations with complex billing operations, multi-entity structures, and dedicated RevOps teams.

---

## 🟩 Open-Source Software

Self-hosted, community-driven Metered and Consumption Billing tools. The open-source ecosystem has matured significantly, with OpenMeter and Lago leading adoption.

### OpenMeter
**Stack:** Go / PostgreSQL / ClickHouse / Kafka | **License:** Apache-2.0
OpenMeter is the leading open-source metering and billing engine for AI, API, and usage-based products, with a stack optimized for high-volume event ingestion and real-time aggregation [citation:3][citation:14]. Key capabilities include:
- **Usage Metering**: Ingest events in CloudEvents format, define meters with flexible aggregations (SUM, COUNT, AVG, MIN, MAX), and query usage in real time [citation:3]
- **Usage-Based Billing**: Generate invoices from metered usage with tiered, graduated, and flat-fee pricing [citation:3]
- **Usage Limits and Entitlements**: Enforce usage quotas per feature with real-time balance tracking, boolean feature flags, and grace periods [citation:3]
- **Product Catalog**: Define plans, add-ons, features, and rate cards with mid-cycle changes, prorating, and alignment [citation:3]
- **Prepaid Credits**: Support paid or promotional credit grants with priority-based burn-down and expiration [citation:3]
- **LLM Cost Tracking**: First-class support for metering AI token usage and computing model-specific costs [citation:3]
- **Customer Portal**: Token-based self-service dashboards so customers can see their own usage [citation:3]

The architecture uses PostgreSQL for billing, subscriptions, and entitlements; ClickHouse for real-time usage aggregation; and Kafka for event streaming [citation:3]. Deploys via Docker Compose (`docker compose up -d`) or Kubernetes Helm chart [citation:3][citation:14]. **Important:** Releases are beta and can include breaking changes, though the metering engine has run in production for years processing billions of events [citation:14].
**Best for:** Teams building AI, agentic, or DevTool products that need real-time metering with Apache-2.0 licensing and no AGPL obligations.

### Lago
**Stack:** Ruby / PostgreSQL / Redis / ClickHouse | **License:** AGPL-3.0
Lago is the most widely adopted open-source billing platform for usage-based, subscription, and hybrid pricing. It handles event ingestion, billable metrics, plans, and invoicing, and pushes invoices to Stripe, Adyen, or GoCardless for collection. Lago is the strongest choice when subscription logic is the core and usage layers on top, or when you need a proven billing engine with a large community. **Trade-off:** AGPL licensing and the operational overhead of running the full stack.

### Flexprice
**Stack:** Go / TypeScript / Docker | **License:** AGPL-3.0
Flexprice is an open-source usage-based pricing and billing platform for developers, with **6,883 GitHub stars** and active development [citation:4]. Key features include real-time usage metering, credits and top-ups, feature access control, a no-code UI, and cloud or self-hosted deployment [citation:4]. SDKs are available for Python, Go, and JavaScript, along with an MCP server for AI agent integration [citation:4]. It is positioned as a developer-friendly alternative with a modern Go backend.
**Best for:** Developers wanting a modern, actively developed open-source metering platform with SDKs and a no-code UI, accepting AGPL licensing.

### Kill Bill (Aviate Metering)
**Stack:** Java / MySQL/MariaDB/PostgreSQL | **License:** Apache-2.0
Kill Bill is a mature open-source billing engine (Apache-2.0, in production since 2010) that supports **usage billing per subscription** through its usage API, rating usage against the catalog at invoice time with tiers, volume pricing, or per-unit rates [citation:7]. For raw event ingestion and aggregation, the commercial **Aviate Metering** add-on ingests raw usage events and aggregates them per billing period with billing meters, so you do not build the aggregation layer yourself [citation:7]. Kill Bill can also handle prepaid credit draw-down through the Aviate Wallet [citation:7]. **Trade-off:** Raw event metering requires the commercial Aviate add-on; the open-source engine handles usage recorded per subscription rather than high-volume raw events.
**Best for:** Teams wanting a permissively licensed (Apache-2.0) billing engine with proven scale and operational maturity, accepting the commercial add-on for high-volume raw event metering.

### Portcall
**Stack:** Go / PostgreSQL / TypeScript/React / Docker | **License:** Open Source (GitHub)
Portcall is an open-source, developer-first platform for **metered billing, entitlements, and feature management** [citation:9]. Key features include metered and subscription billing (usage-based, seat-based), entitlement management (feature flags, quotas, limits), modern APIs (REST, webhooks, event-driven), and a dashboard built with Vite and React [citation:9]. The architecture uses Go microservices, PostgreSQL, Keycloak for auth, and a queue system, with a monorepo structure [citation:9].
**Best for:** Teams wanting an open-source platform combining metered billing with entitlement and feature management in one system, accepting a newer project than OpenMeter or Lago.

---

## 📊 Comparison at a Glance

| Software | License | Stack | Real-Time Metering | Prepaid Credits | LLM Token Tracking | Self-Hosted | Best For |
|----------|---------|-------|-------------------|-----------------|-------------------|-------------|----------|
| **Metronome** | Proprietary | Cloud | ✅ High-volume | (Check) | (Check) | ❌ | Stripe ecosystem rating |
| **Orb** | Proprietary | Cloud | ✅ Multi-dimensional | (Check) | (Check) | ❌ | Adyen ecosystem pricing |
| **Chargebee** | Proprietary | Cloud | (Add-on) | ✅ | (Via events) | ❌ | Existing Chargebee users |
| **Amberflo** | Proprietary | Cloud | ✅ Event-first | ✅ | ✅ | ❌ | Independent metering-first |
| **OpenMeter** | Apache-2.0 | Go/ClickHouse/Kafka | ✅ Real-time | ✅ Burn-down | ✅ First-class | ✅ | OSS metering + LLM |
| **Lago** | AGPL-3.0 | Ruby/Postgres | ✅ Real-time | ✅ | (Via events) | ✅ | Proven OSS billing |
| **Flexprice** | AGPL-3.0 | Go/TypeScript | ✅ Real-time | ✅ | (Check) | ✅ | Developer-friendly OSS |
| **Kill Bill** | Apache-2.0 | Java/DB | (Via Aviate) | ✅ Aviate Wallet | ❌ | ✅ | Permissive OSS engine |
| **Portcall** | Open Source | Go/Postgres | ✅ | (Check) | ❌ | ✅ | Billing + entitlements |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source Metered or Consumption Billing tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source (or clearly note if it is source-available but not OSI-approved).

**Note on the open-source ecosystem:** The **commercial landscape shifted dramatically in 2026** — the major independent metering vendors were acquired: Stripe took Metronome, Salesforce took m3ter, and Adyen took Orb. This makes **licence independence** the most durable form of control: OpenMeter (Apache 2.0) and Lago (AGPL) cannot be revoked by acquisition, even if their commercial stewards change. **OpenMeter** is the strongest choice for AI/LLM token metering with first-class support and a high-volume architecture built on Kafka, ClickHouse, and PostgreSQL [citation:3][citation:14]. **Lago** offers the most mature open-source billing engine with proven deduplication and late-event handling. **Flexprice** is a strong developer-friendly alternative with a modern Go stack and SDKs [citation:4]. **Kill Bill** remains the most permissively licensed option for teams wanting to own their billing infrastructure, with commercial Aviate Metering available for high-volume raw event ingestion [citation:7]. **Amberflo** remains the notable independent commercial option for metering-first architectures.

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
