# Awesome E-commerce and Retail Tools & Workflow

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: CC0-1.0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](http://creativecommons.org/publicdomain/zero/1.0/)

A curated list of **production-grade open-source projects** for building, running, and scaling e-commerce and retail operations. Covers the full stack — from storefront to fulfillment, from product data to marketing automation.

> **What this is not**: a list of every e-commerce project on GitHub. A generic dev-tool list. A vendor directory. We focus on **tools you can self-host, fork, or integrate today**, plus the **workflows that connect them**.

---

## Table of Contents

1. [How to Choose (Decision Matrix)](#how-to-choose-decision-matrix)
2. [Storefront & Commerce Platforms](#1-storefront--commerce-platforms)
3. [Order, Inventory & Warehouse](#2-order-inventory--warehouse)
4. [Product Information Management (PIM)](#3-product-information-management-pim)
5. [Point of Sale (POS)](#4-point-of-sale-pos)
6. [Payments & Orchestration](#5-payments--orchestration)
7. [Search, Discovery & Recommendations](#6-search-discovery--recommendations)
8. [Customer Data, Marketing & Support](#7-customer-data-marketing--support)
9. [Analytics, BI & Data Stack](#8-analytics-bi--data-stack)
10. [End-to-End Workflows](#9-end-to-end-workflows)
11. [Contributing](#contributing)

---

## How to Choose (Decision Matrix

Picking a tool without picking a job is how you end up with 14 dashboards and zero orders shipped. Start with the **job**, then the **deployment shape**, then the tool.

| If you need to… | Start with | Why |
|---|---|---|
| Launch a B2C store fast, low traffic | **WooCommerce** or **PrestaShop** | PHP, shared-hosting friendly, huge plugin ecosystem |
| Build a custom headless storefront on Node/TS | **Medusa** or **Vendure** | API-first, modular, both MIT |
| Build a high-throughput store on Python | **Saleor** | GraphQL-first, Kubernetes-friendly |
| Build a B2B / multi-vendor / marketplace | **Vendure** or **Medusa** | Both model B2B and marketplaces as first-class |
| Centralize product data, then syndicate | **Akeneo PIM Community** | The de-facto open PIM |
| Run a physical store or chain | **Odoo POS** or **uniCenta** | Odoo = full ERP+POS; uniCenta = pure POS |
| Orchestrate payments across many gateways | **Hyperswitch** | Open-source Stripe-orchestrator alternative |
| Add typo-tolerant search to a catalog | **Meilisearch** or **Typesense** | Both blazing fast, both MIT |
| Track customers, run email/SMS campaigns | **Mautic** | Open HubSpot/ActiveCampaign alternative |
| Build a customer support inbox | **Chatwoot** | Open Intercom/Zendesk alternative |
| Visualize sales/funnel data | **Metabase** or **Apache Superset** | Both MIT, both connect to every warehouse |

> **Rule of thumb**: prefer MIT / Apache-2.0 unless you have a strong reason. Be cautious with AGPL projects for SaaS (network copyleft).

---

## 1. Storefront & Commerce Platforms

The core: a system of record for products, orders, customers, and checkout. Pick headless if you want full frontend control; pick monolithic if you want everything in one box.

### Headless / API-first

- **[Medusa](https://github.com/medusajs/medusa)** — Node.js/TypeScript headless commerce engine. Modular, plugin-based, MIT. The fastest-growing open commerce project. Use when: you want to build a custom store on Node and keep all commerce logic separate from your frontend.
- **[Saleor](https://github.com/saleor/saleor)** — Python/GraphQL composable commerce platform. Kubernetes-native, BSD-3. Use when: you want GraphQL-first, high throughput, and a strong order/cart/promotion engine out of the box.
- **[Vendure](https://github.com/vendurehq/vendure)** — TypeScript/NestJS headless commerce framework. Plugin marketplace, multi-channel, B2B-friendly, MIT. Use when: you need a B2B-grade commerce backend with strong extensibility.
- **[Spree](https://github.com/spree/spree)** — Rails-based headless commerce with REST API + TypeScript SDK + Next.js storefront, BSD-3. Use when: you want a mature Ruby option with cross-border and marketplace support.

### Monolithic / All-in-one

- **[WooCommerce](https://github.com/woocommerce/woocommerce)** — WordPress ecommerce plugin, GPL. The largest install base of any ecommerce platform on the planet. Use when: you already have a WordPress site, or you want a low-friction SMB launch.
- **[PrestaShop](https://github.com/PrestaShop/PrestaShop)** — PHP ecommerce platform, OSL-3.0. Strong in EU, large module marketplace. Use when: you want a self-contained store with deep product/catalog features.
- **[Shopware 6](https://github.com/shopware/shopware)** — PHP/Symfony + Vue.js open commerce platform, MIT. Enterprise-grade, strong in DACH region. Use when: you want Symfony extensibility and a mature plugin ecosystem.
- **[nopCommerce](https://github.com/nopsolutions/nopcommerce)** — ASP.NET Core ecommerce, GPL-3.0. Use when: your stack is .NET and you want a full-featured store out of the box.
- **[Bagisto](https://github.com/bagisto/bagisto)** — Laravel-based ecommerce, MIT. Multi-warehouse, multi-currency, multi-channel. Use when: you love Laravel and want a modern PHP alternative to PrestaShop/Magento.

### Specialized

- **[Pretix](https://github.com/pretix/pretix)** — Python ticket-shop for events/festivals/conferences, AGPL-3.0 with commercial license. Use when: you sell tickets, not physical goods.
- **[Aimeos](https://github.com/aimeos/aimeos-laravel)** — Ultra-fast Laravel ecommerce framework, MIT. Use when: you need to scale to huge catalogs and complex B2B pricing.

---

## 2. Order, Inventory & Warehouse

The supply chain layer: track what you have, where it is, and when it ships.

### Order Management (OMS)

- **[Apache OFBiz](https://github.com/apache/ofbiz-framework)** — Java ERP/CRM/OMS suite, Apache-2.0. 20+ years mature. Use when: you need a full enterprise process suite, not just a store.
- **[ERPNext](https://github.com/frappe/erpnext)** — Python/Frappe full ERP with built-in OMS, GPL-3.0. No per-user pricing. Use when: you want ERP + OMS + accounting in one stack.
- **[Odoo (Community)](https://github.com/odoo/odoo)** — Python full ERP, LGPL-3.0. Massive app marketplace. Use when: you want the broadest open-source business app catalog.

### Inventory Management (IMS)

- **[InvenTree](https://github.com/inventree/inventree)** — Python/Django inventory + BOM management, MIT. Lightweight, REST API, great for SME / maker / hardware. Use when: you track physical parts, not just finished SKUs.
- **[OpenBoxes](https://github.com/openboxes/openboxes)** — Java supply-chain IMS, EPL-1.0. Designed for healthcare/distribution in low-resource settings. Use when: you need batch tracking and multi-warehouse.

### Warehouse Management (WMS)

- **[OpenWMS.org](https://github.com/openwms/org.openwms)** — Java/Spring Boot microservices WMS, Apache-2.0. Material flow control + ERP integration. Use when: you need real warehouse automation (conveyors, PLCs).
- **[ModernWMS](https://github.com/fjykTec/ModernWMS)** — .NET 7 + Vue 3 WMS, MIT. Simpler entry point, cross-platform. Use when: you want a self-host WMS in days, not months.

---

## 3. Product Information Management (PIM)

Centralize product data — descriptions, attributes, media, classifications — and syndicate to storefronts, marketplaces, and catalogs.

- **[Akeneo PIM Community](https://github.com/akeneo/pim-community-dev)** — PHP/Symfony PIM, MIT for Community Edition. Industry standard open PIM. Use when: your product complexity (variants, channels, locales) is outgrowing your commerce DB.
- **[Pimcore](https://github.com/pimcore/pimcore)** — PHP/ Symfony MDM + PIM + DAM + CMS, GPL-3.0. Use when: you need master data management beyond just products (assets, customers, suppliers).
- **[Reactium CMS](https://github.com/codex-team/reactium)** *(add only if PIM-shaped; placeholder for discovery)*

> **What goes here but isn't open source**: Salsify, Censhare, inriver. Listed for context, not included.

---

## 4. Point of Sale (POS)

Run a physical store, restaurant, or pop-up without giving up control of your data.

- **[uniCenta oPOS](https://github.com/unicentaopos/unicentaopos)** — Java Swing POS, GPL-3.0. Battle-tested, multi-terminal. Use when: you need a desktop POS that works offline.
- **[Open Source POS (OSPOS)](https://github.com/opensourcepos/opensourcepos)** — PHP/CodeIgniter web POS, MIT. Browser-based, low hardware requirements. Use when: you want a web POS that runs on cheap hardware.
- **[Odoo POS](https://github.com/odoo/odoo)** — Same Odoo as above; POS module is LGPL. Use when: you want POS + inventory + accounting in one place.
- **[Flarepoint POS](https://github.com/Flarepoint/Flarepoint)** — PHP/Laravel POS, MIT. Lightweight SMB option. *(Verify activity before relying on.)*

---

## 5. Payments & Orchestration

Take money without depending on a single processor.

### Payment Orchestration

- **[Hyperswitch](https://github.com/juspay/hyperswitch)** — Rust payment orchestrator, Apache-2.0. Connects 100+ processors, smart routing, retries, cost observability. Use when: you process across multiple gateways and want one API.

### Payment Processors / Gateways (self-host)

- **[Solidus](https://github.com/solidusio/solidus)** — Ruby on Rails ecommerce framework with a flexible payment architecture, BSD-3. Use when: you need a programmable payment backend.
- **[Keagate](https://github.com/dilan-dio4/keagate)** — TypeScript crypto payment gateway, MIT. Use when: you accept crypto.

> **Note**: Most payment processors are SaaS-only (Stripe, Adyen, Checkout.com). For card storage in a self-hosted stack, pair Hyperswitch + a PCI-compliant vault.

---

## 6. Search, Discovery & Recommendations

Make the catalog findable. The difference between a 2% and 8% conversion rate often lives here.

### Search Engines

- **[Meilisearch](https://github.com/meilisearch/meilisearch)** — Rust in-memory typo-tolerant search, MIT. Easy to deploy, instant search. Use when: you want Algolia-quality UX with self-host.
- **[Typesense](https://github.com/typesense/typesense)** — C++ search engine, Apache-2.0. Vector search, semantic search, geo search. Use when: you need vector + keyword hybrid with Algolia-like UX.
- **[OpenSearch](https://github.com/opensearch-project/OpenSearch)** — Apache-2.0, Elasticsearch fork. Use when: you need full-text + analytics + log search on one cluster.

### Recommender Systems

- **[LightFM](https://github.com/lyst/lightfm)** — Python hybrid recommender (CF + content), MIT. Use when: you have user-item interaction data and product metadata.
- **[RecBole](https://github.com/recbole/recbole)** — PyTorch unified recommender library, MIT. 100+ models. Use when: you want a research-grade benchmark to pick the right algorithm.
- **[Towhee](https://github.com/towhee-io/towhee)** — Python embedding pipeline for unstructured data, Apache-2.0. Use when: you need vector pipelines for product/content embeddings.
- **[Gorse](https://github.com/gorse-io/gorse)** — Go recommender as a service, Apache-2.0. Auto-train, auto-deploy. Use when: you want a self-host "set it and forget it" recs service.

---

## 7. Customer Data, Marketing & Support

The post-purchase half of the funnel. Acquire, retain, support.

### Marketing Automation

- **[Mautic](https://github.com/mautic/mautic)** — PHP marketing automation, GPL-3.0. Email, SMS, social, campaigns, lead scoring. Use when: you want HubSpot/ActiveCampaign with full data ownership.
- **[Listmonk](https://github.com/knadh/listmonk)** — Go newsletter + mailing list manager, AGPL-3.0. High-performance, self-host. Use when: your main job is sending newsletters at scale.

### Customer Support / Helpdesk

- **[Chatwoot](https://github.com/chatwoot/chatwoot)** — Rails omnichannel support (live chat, email, social, WhatsApp), MIT. Use when: you want a self-host Intercom/Zendesk with built-in AI agent (Captain).
- **[FreeScout](https://github.com/freescout-help-desk/freescout)** — PHP helpdesk, AGPL-3.0. Lightweight Zendesk alternative. Use when: you only need shared inbox + help center, no live chat.
- **[Zammad](https://github.com/zammad/zammad)** — Rails helpdesk, AGPL-3.0. Multi-channel, strong ticket workflows. Use when: you need a mature ITSM-style ticket system.

### Live Chat (for the storefront)

- **[Rocket.Chat](https://github.com/RocketChat/RocketChat)** — Node.js team chat, MIT. Many use it as a customer chat backend. *(Use for omnichannel customer chat only when you also want internal team chat.)*

---

## 8. Analytics, BI & Data Stack

Look at the numbers, ship the next decision.

### BI / Dashboards

- **[Metabase](https://github.com/metabase/metabase)** — Clojure/JS BI, AGPL-3.0 (commercial license available). Easiest UX, connects to every DB. Use when: non-technical people need to answer their own questions.
- **[Apache Superset](https://github.com/apache/superset)** — Python BI, Apache-2.0. More flexible, supports more chart types. Use when: you need embedded analytics or custom visualizations.
- **[Lightdash](https://github.com/lightdash/lightdash)** — TypeScript BI built for dbt, MIT. Use when: your data team lives in dbt.
- **[Redash](https://github.com/getredash/redash)** — Python BI, BSD-2. Use when: you want SQL-first, simple dashboards.

### Data Movement

- **[Airbyte](https://github.com/airbytehq/airbyte)** — ELT platform, ELv2. 300+ connectors. Use when: you need to pipe Stripe, Shopify, GA into your warehouse.
- **[Meltano](https://github.com/meltano/meltano)** — Python ELT, Apache-2.0. Singer-spec based, CLI-first. Use when: you prefer Singer taps/targets.
- **[dbt](https://github.com/dbt-labs/dbt-core)** — SQL transformation framework, Apache-2.0. Use when: you want version-controlled, tested transformations in your warehouse.

---

## 9. End-to-End Workflows

These aren't tools — they're patterns. How the pieces fit together.

### Workflow A — Headless DTC Store

**Goal**: launch a custom-storefront brand in weeks, not quarters.

```
Storefront (Next.js) ──► Medusa or Saleor (commerce API)
                            │
                            ├──► Akeneo PIM (product data)
                            ├──► Meilisearch (search)
                            ├──► Hyperswitch (payments)
                            ├──► Mautic (email/SMS)
                            ├──► Chatwoot (support widget)
                            └──► Metabase (analytics)
```

**Why this works**: each piece is MIT/Apache, can be swapped, and you keep the storefront fully custom.

### Workflow B — Multi-Store Retailer

**Goal**: one commerce backend, many storefronts (web, POS, B2B portal, marketplace).

```
Odoo or ERPNext (master data + OMS)
    │
    ├──► WooCommerce (consumer storefront)
    ├──► Odoo POS (physical stores)
    ├──► Medusa (B2B portal)
    ├──► Pretix (events)
    └──► Airbyte → BigQuery → Metabase (BI)
```

**Why this works**: Odoo/ERPNext acts as the system of record, each channel picks the best tool.

### Workflow C — Marketplace / B2B Platform

**Goal**: enable many sellers, one checkout experience.

```
Vendure or Medusa (multi-vendor commerce)
    │
    ├──► Stripe Connect / Hyperswitch (split payouts)
    ├──► Chatwoot (per-seller support)
    ├──► Mautic (per-segment marketing)
    ├──► Gorse (per-seller recs)
    └──► Apache Superset (operator analytics)
```

**Why this works**: both Vendure and Medusa have first-class multi-vendor/marketplace primitives.

### Workflow D — Physical + Online (Unified Commerce)

**Goal**: one inventory, one customer view, store and online merged.

```
Odoo (ERP + IMS + POS)
    │
    ├──► Odoo eCommerce (online storefront)
    ├──► Odoo POS (in-store)
    ├──► OpenWMS (warehouse)
    ├──► Mautic (marketing, unified customer view)
    └──► Metabase (KPIs)
```

**Why this works**: Odoo's strength is exactly this — single source of truth across all channels.

---

## Contributing

Contributions welcome. Please read:

1. **The project must be open source** with a license in the repo.
2. **Stars ≥ 500** unless it fills a unique gap (call out why in the PR).
3. **Commits within the last 12 months** unless explicitly archived-mature.
4. **Real retail/ecommerce relevance** — not generic dev tooling.
5. Format: `**Name** — one-line description. License. Use when: …`

Open a PR with your addition. Tag the category. Explain the "why" in 1-2 sentences.

---

## License

[CC0 1.0](http://creativecommons.org/publicdomain/zero/1.0/) — public domain. Take it, fork it, embed it in your training set, whatever.
