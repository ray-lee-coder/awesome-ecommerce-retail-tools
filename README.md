# Awesome E-commerce & Retail: Small Tools & Workflow Recipes

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: CC0-1.0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](http://creativecommons.org/publicdomain/zero/1.0/)

A curated list of **small, focused open-source tools** for people actually running e-commerce and retail — Amazon sellers, Shopify merchants, DTC operators, cross-border resellers, small-store owners.

> **What's here**: a single-purpose tool you can `git clone` and use in an afternoon. A scraper for one marketplace. A review-alert bot. A price tracker. A listing copy helper. A Telegram shop bot. A price-formatting Snippet.
>
> **What's NOT here**: full commerce platforms (Medusa, Saleor, Shopware, ERPNext), AI workflow builders as products (n8n, Dify, Coze, Flowise, Langflow), base engines (ComfyUI, Ollama, LlamaIndex), and BI platforms (Metabase, Superset, PostHog). Those are upstream of the work — this list is for **tools you plug in, not platforms you build on**.

---

## Table of Contents

1. [Picking a Tool (Decision Matrix)](#picking-a-tool-decision-matrix)
2. [Amazon Seller Tools](#1-amazon-seller-tools)
3. [Shopify, WooCommerce & Storefront Tooling](#2-shopify-woocommerce--storefront-tooling)
4. [Cross-Marketplace Scrapers & Trackers](#3-cross-marketplace-scrapers--trackers)
5. [Pricing, Repricing & Margin](#4-pricing-repricing--margin)
6. [Reviews, Ratings & Customer Insight](#5-reviews-ratings--customer-insight)
7. [Listings, Copy & SEO Helpers](#6-listings-copy--seo-helpers)
8. [Marketing & Ad Creative](#7-marketing--ad-creative)
9. [Inventory, Orders & Fulfillment](#8-inventory-orders--fulfillment)
10. [Messaging Bots & Customer Touchpoints](#9-messaging-bots--customer-touchpoints)
11. [Marketplace Connectors & API Wrappers](#10-marketplace-connectors--api-wrappers)
12. [Workflow Recipes](#11-workflow-recipes)
13. [Contributing](#contributing)

---

## Picking a Tool (Decision Matrix

| You want to… | Try | Notes |
|---|---|---|
| Track one Amazon product's price over time | `omerhalid/Amazon-Price-Tracker` (Python script) | Smallest path; cron + email |
| Track prices across many products and many sites | `dgtlmoon/changedetection.io` | Self-host, visual diff, alerts |
| Pull Amazon search results / best-sellers into a CSV | `oxylabs/amazon-scraper` (free CLI) | Works without API key for small batches |
| Talk to Amazon Seller Central from a script or AI | `jay-trivedi/amazon_sp_mcp` | MCP server, plug into Claude/Cursor |
| Find winning keywords for an Amazon listing | `sonarspeed` (SaaS) — for OSS: scrape + spaCy + BERTopic | See [recipe](#workflow-recipes) |
| Auto-translate / rewrite a product description | `video-lingo` / `MoneyPrinterTurbo` (broader, but for text: any LLM + MarkItDown) | Local first, paid if needed |
| Get a Telegram alert on every new review | `Telegram-Bot` boilerplate + scraper cron | Recipe below |
| Get notified of low-stock on Shopify | `inventree-shopify` (sync) or `Shopify Webhook` + Slack | Recipe below |
| Build a self-hosted Shopify app in 10 minutes | `Shopify/shopify-app-template-remix` | Official starter |
| Build a Telegram shop from scratch | `ilyarolf/AiogramShopBot` | Production-style, crypto-ready |
| Run a single-purpose scraper for AliExpress / Taobao / 1688 | dedicated scraper repos (see §3) | English UI is hit-or-miss |

> **How to read this list**: each entry is one job. If the tool has more than ~3 major capabilities, it's probably a platform and shouldn't be here.

---

## 1. Amazon Seller Tools

The most crowded ecosystem. Below = open-source / small.

- **[oxylabs/amazon-scraper](https://github.com/oxylabs/amazon-scraper)** — Free CLI scraper for Amazon department / product / search / reviews. Apache-2.0. Use when: you want a script that pulls product data without an API key for small jobs.
- **[oxylabs/amazon-asin-scraper](https://github.com/oxylabs/amazon-asin-scraper)** — Batch ASIN → product details (price, stock, offers, reviews). Apache-2.0. Use when: you have a list of ASINs and want structured data.
- **[omerhalid/Amazon-Price-Tracker](https://github.com/omerhalid/Amazon-Price-Tracker)** — Python script: monitor one product, email when price drops. Use when: you track 1-10 SKUs personally.
- **[dgtlmoon/changedetection.io](https://github.com/dgtlmoon/changedetection.io)** — Self-host page-change monitor with alerts (price, stock, content). Apache-2.0. Use when: you want visual diff + email/Slack/Telegram alerts on competitor pages.
- **[jay-trivedi/amazon_sp_mcp](https://github.com/jay-trivedi/amazon_sp_mcp)** — MCP server for Amazon SP-API, MIT. Use when: you want Claude / Cursor / Codex to read your Seller Central data.
- **[dgtlmoon/changedetection.io (Amazon discussion)](https://github.com/dgtlmoon/changedetection.io/discussions/2398)** — Community thread for Amazon price-drop recipes. Use when: you need example selectors.
- **[scrapehero-code/amazon-review-scraper](https://github.com/scrapehero-code/amazon-review-scraper)** — Amazon review scraper using Selectorlib. Use when: you need a few thousand reviews into CSV.
- **[omkarcloud/amazon-scraper](https://github.com/omkarcloud/amazon-scraper)** — High-level Amazon product scraper, MIT. Use when: you want clean JSON, no proxy setup.
- **[Decodo/Amazon-scraper](https://github.com/Decodo/Amazon-scraper)** — Simple Amazon search → CSV. Use when: you just need a one-off.
- **[Price-Tracking-Web-Scraper (techwithtim)](https://github.com/techwithtim/Price-Tracking-Web-Scraper)** — UI-based Amazon price tracker. Use when: you want a web UI without writing one.

### Related, smaller utilities

- **[awesome-amazon-seller (ScaleLeap)](https://github.com/ScaleLeap/awesome-amazon-seller)** — A list of tools (mostly SaaS) for Amazon sellers. Use when: you want a market map of the SaaS landscape to know what to replace.
- **[nexscope-ai/awesome-amazon-seller-tools](https://github.com/nexscope-ai/awesome-amazon-seller-tools)** — Similar, more AI-agent focused.
- **[smart-seller/awesome-amazon-seller-tools](https://github.com/smart-seller/awesome-amazon-seller-tools)** — Marketing / optimization focused.

---

## 2. Shopify, WooCommerce & Storefront Tooling

- **[Shopify/shopify-app-template-remix](https://github.com/Shopify/shopify-app-template-remix)** — Official Shopify Remix app template. MIT. Use when: you build a custom Shopify app.
- **[Shopify/shopify-app-template-node](https://github.com/Shopify/shopify-app-template-node)** — Official Node + React template. MIT. Use when: you prefer Node.
- **[Shopify/theme-extension-getting-started](https://github.com/Shopify/theme-extension-getting-started)** — Theme app extension boilerplate. MIT. Use when: you build a theme extension.
- **[Shopify/extensions-templates](https://github.com/Shopify/extensions-templates)** — All Shopify extension templates (checkout UI, POS, etc.). MIT.
- **[inventree-shopify](https://github.com/invenhost/inventree-shopify)** — Sync stock between InvenTree and Shopify. Use when: you want a self-host stock + Shopify front.
- **[julionc/awesome-shopify](https://github.com/julionc/awesome-shopify)** — A list of Shopify resources, libraries, and OSS projects. Use when: you want a market map of the Shopify ecosystem.

---

## 3. Cross-Marketplace Scrapers & Trackers

- **[oxylabs/ecommerce-category-scraper](https://github.com/oxylabs/ecommerce-category-scraper)** — AI-powered category & price scraping templates. Apache-2.0.
- **[sudheer-ranga/aliexpress-product-scraper](https://github.com/sudheer-ranga/aliexpress-product-scraper)** — AliExpress → JSON (feedbacks, variants, shipping). Use when: you dropship or source from AliExpress.
- **[omkarcloud/aliexpress-scraper](https://github.com/omkarcloud/aliexpress-scraper)** — Clean API-style AliExpress scraper. Use when: you want reliable product data.
- **[wfgsss/pinduoduo-scraper-example](https://github.com/wfgsss/pinduoduo-scraper-example)** — Pinduoduo (拼多多) product scraper. Use when: you source from Pinduoduo.
- **[phariel/taobao-reseller-tools](https://github.com/phariel/taobao-reseller-tools)** — Taobao reseller helper scripts. Use when: you buy from Taobao and resell.
- **[dtapps/go-library pinduoduo](https://pkg.go.dev/github.com/dtapps/go-library/service/pinduoduo)** — Go client for Pinduoduo open API. Use when: you build Pinduoduo tooling in Go.
- **[omkarcloud/amazon-scraper](https://github.com/omkarcloud/amazon-scraper)** — *(also in §1; listed here as cross-marketplace)*
- **[Crawlee](https://github.com/apify/crawlee)** — Node.js / Python scraping + browser-automation library. Apache-2.0. Use when: you build a serious scraper, not a one-off. *(engineering-grade, not a finished tool — used to make tools.)*
- **[AutoScraper](https://github.com/alirezamika/autoscraper)** — Learn-to-scrape with a few examples. MIT. Use when: you want quick-and-dirty without LLM.
- **[ScrapeGraphAI](https://github.com/ScrapeGraphAI/ScrapeGraphAI)** — LLM-driven structured extractor ("extract the price + SKU"). MIT. Use when: pages are weird and you don't want to write selectors.
- **[Browse AI CLI](https://github.com/browse-ai/browseai-cli)** — Record a robot scraping a page, replay on schedule. MIT.
- **[Firecrawl](https://github.com/mendableai/firecrawl)** — URL → clean markdown/JSON for LLMs. AGPL-3.0. Use when: you want to feed any site into a workflow.
- **[Crawl4AI](https://github.com/unclecode/crawl4ai)** — Self-host LLM-friendly crawler. Apache-2.0. Use when: you don't want to depend on Firecrawl's cloud.
- **[Jina Reader](https://github.com/jina-ai/reader)** — URL → clean LLM text. Apache-2.0. Use when: you want a 1-line API for "give me the readable text".

---

## 4. Pricing, Repricing & Margin

- **[omerhalid/Amazon-Price-Tracker](https://github.com/omerhalid/Amazon-Price-Tracker)** — *(also in §1)* — for personal Amazon tracking.
- **[dgtlmoon/changedetection.io](https://github.com/dgtlmoon/changedetection.io)** — *(also in §1)* — for multi-site tracking.
- **[dataprice (Glitchero)](https://github.com/Glitchero/dataprice)** — Open-source competitor price tracker. Use when: you want a self-host engine.
- **[Amazon-Price-Tracker (rajitbanerjee)](https://github.com/rajitbanerjee/amazon-price-tracker)** — Amazon UK scraper, MIT.
- **[younesaitmha/amazon-price-tracker](https://github.com/younesaitmha/amazon-price-tracker)** — Django + BeautifulSoup tracker, MIT.
- **[coderj001/Amazon-Price-Tracker](https://github.com/coderj001/Amazon-Price-Tracker)** — Selenium-based, MIT.
- **[TrackItNow (Rahulnisanth)](https://github.com/Rahulnisanth/TrackItNow)** — Multi-product e-commerce tracker, MIT.

> **For Amazon repricing at scale**: there's no fully open-source production-grade repricer. The market is dominated by Helium 10 / Sellerboard / RepricerExpress. Open-source tools above are good for personal or sub-100-SKU use.

---

## 5. Reviews, Ratings & Customer Insight

- **[scrapehero-code/amazon-review-scraper](https://github.com/scrapehero-code/amazon-review-scraper)** — *(see §1)*
- **[VADER](https://github.com/cjhutto/vaderSentiment)** — Rule-based sentiment, MIT. Drop-in for review scoring.
- **[TextBlob](https://github.com/sloria/TextBlob)** — Simple NLP, MIT. Use when: you want a quick sentiment score.
- **[spaCy](https://github.com/explosion/spaCy)** — Industrial NLP, MIT. Use when: you build a real review pipeline.
- **[BERTopic](https://github.com/MaartenGr/BERTopic)** — Cluster reviews into themes. MIT. Use when: you have 10k+ reviews and want to know what people complain about.
- **[allenyan513/reviewsup.io](https://github.com/allenyan513/reviewsup.io)** — Open-source review & testimonial management system. Use when: you want a self-host Trustpilot alternative.
- **[Argilla](https://github.com/argilla-io/argilla)** — Data labeling for LLM, Apache-2.0. Use when: you curate a review dataset for eval.
- **[Cleanlab](https://github.com/cleanlab/cleanlab)** — Find label issues, MIT. Use when: you have a tagged review dataset.
- **[Jina Reader](https://github.com/jina-ai/reader)** — *(also in §3)* — turn a review page into LLM text for sentiment / summarization.

---

## 6. Listings, Copy & SEO Helpers

> These are the *small* tools; full AI listing optimizers are SaaS (Helium 10 Scribbles, Jungle Scout, etc.) and out of scope.

- **[MarkItDown](https://github.com/microsoft/markitdown)** — Convert any file (PDF, DOCX, HTML, images) → Markdown. MIT. Use when: supplier sends you a PDF catalog and you need structured text.
- **[Surya](https://github.com/VikParuchuri/surya)** — 90+ language OCR with layout, GPL-3.0. Use when: you extract text from product images, scans, supplier photos.
- **[Marker](https://github.com/datalab-to/marker)** — Fast PDF / image → Markdown, Apache-2.0.
- **[PaddleOCR](https://github.com/PaddlePaddle/PaddleOCR)** — Multilingual OCR, Apache-2.0. Use when: you OCR product labels in CN/KR/JP/TH.
- **[Jina Reader](https://github.com/jina-ai/reader)** — *(see §3)* — turn competitor product pages into LLM-readable text for analysis / rewriting.
- **[ScrapeGraphAI](https://github.com/ScrapeGraphAI/ScrapeGraphAI)** — *(see §3)* — extract structured listing fields with one prompt.
- **[Firecrawl](https://github.com/mendableai/firecrawl)** — *(see §3)* — same use case at scale.

> **For Amazon listing copy generation**: pipe any of the above scrapers into a local Ollama/OpenAI call with a prompt like "rewrite this title to include keywords X, Y, Z while staying under 200 chars". No dedicated open-source tool does this end-to-end — it's a 20-line script.

---

## 7. Marketing & Ad Creative

> Focused on **small** tools. Big BI / analytics / marketing platforms are out of scope (see PostHog / Plausible / Metabase elsewhere).

- **[MoneyPrinterTurbo](https://github.com/harry0703/MoneyPrinterTurbo)** — One-click short video from a topic, Apache-2.0. Use when: you batch-generate product promo videos.
- **[VideoLingo](https://github.com/HKUDS/VideoLingo)** — Auto-dub, subtitle, translate video, Apache-2.0. Use when: you localize product video.
- **[Ghostwriter-LLM (robgraham)](https://github.com/robgraham/ghostwriter-llm)** — WordPress content generator in your brand voice, MIT.
- **[autosub (agermanidis)](https://github.com/agermanidis/autosub)** — Auto subtitle generator, MIT.
- **[Plausible CE](https://github.com/plausible/community-edition)** — Self-host cookieless analytics, AGPL-3.0. Use when: GDPR-clean storefront analytics.
- **[Umami](https://github.com/umami-software/umami)** — Privacy-friendly analytics, MIT.
- **[Open Web Analytics](https://github.com/OpenWebAnalytics/openwebanalytics)** — Self-host web analytics, GPL-2.0.
- **[Postal](https://github.com/postalserver/postal)** — Self-host mail server, MIT. Use when: you self-host all transactional email.
- **[Listmonk](https://github.com/knadh/listmonk)** — High-performance newsletter manager, AGPL-3.0.

> **For ad creative generation**: no production-grade open-source equivalent to AdCreative.ai. The closest is ComfyUI / SD pipelines (out of scope as a base engine) wired into a script.

---

## 8. Inventory, Orders & Fulfillment

- **[InvenTree](https://github.com/inventree/inventree)** — Open-source inventory + BOM, MIT. Use when: you track physical parts, BOMs, builds.
- **[inventree-shopify](https://github.com/invenhost/inventree-shopify)** — *(see §2)* — Shopify stock sync.
- **[OpenBoxes](https://github.com/openboxes/openboxes)** — Open-source supply-chain IMS, EPL-1.0. Use when: healthcare / NGO distribution.
- **[OpenWMS.org](https://github.com/openwms/org.openwms)** — Warehouse management microservices, Apache-2.0. Use when: real warehouse automation.
- **[ModernWMS](https://github.com/fjykTec/ModernWMS)** — Simpler self-host WMS, MIT.

> **For Amazon FBA inbound / shipment**: no good open-source tool. The community lives on Jungle Scout / Helium 10 / Sellerboard.

---

## 9. Messaging Bots & Customer Touchpoints

- **[ilyarolf/AiogramShopBot](https://github.com/ilyarolf/AiogramShopBot)** — Production-style Telegram shop bot (digital + physical goods, crypto payments, admin). MIT. Use when: you sell via Telegram.
- **[interlumpen/Telegram-shop](https://github.com/interlumpen/Telegram-shop)** — Production-ready Telegram shop with security, transactional integrity, admin, monitoring. Use when: you want a hardened Telegram shop.
- **[Telegram-Bot Boilerplates]** — see `telegram-bot` topic on GitHub; pick the one in your language.
- **[Typebot](https://github.com/baptisteArno/typebot)** — Visual conversational form builder, AGPL-3.0. Use when: lead-gen / survey / support in chat UI.
- **[Botpress](https://github.com/botpress/botpress)** — Visual chatbot with NLU, MIT. Use when: you want a self-host ManyChat with real NLU.
- **[Rasa](https://github.com/RasaHQ/rasa)** — Conversational AI framework, Apache-2.0. Use when: full-control NLU.
- **[Chatwoot](https://github.com/chatwoot/chatwoot)** — Omnichannel support inbox, MIT. Use when: a self-host Intercom.
- **[Rocket.Chat](https://github.com/RocketChat/RocketChat)** — Team chat + omnichannel, MIT. Use when: you want Slack/Teams + customer chat.
- **[Vectara ragtime](https://github.com/vectara/ragtime)** — RAG bot for Slack/Discord. Use when: a "chat with your data" bot in chat platforms.

---

## 10. Marketplace Connectors & API Wrappers

> Thin clients around marketplace APIs. Save you weeks of OAuth and pagination work.

- **[jay-trivedi/amazon_sp_mcp](https://github.com/jay-trivedi/amazon_sp_mcp)** — *(see §1)* — MCP server for Amazon SP-API.
- **[DataDoe MCP Server](https://mcpservers.org/servers/deltologic/datadoe-mcp)** — Hosted Amazon SP-API + Ads MCP server, MIT. Use when: you want a managed MCP connection.
- **[dtapps/go-library pinduoduo](https://pkg.go.dev/github.com/dtapps/go-library/service/pinduoduo)** — *(see §3)* — Go Pinduoduo client.
- **[Selling Partner API Models (amzn)](https://github.com/amzn/selling-partner-api-models)** — Official Amazon SP-API Swagger models. Apache-2.0.
- **[Amazon Selling Partner API on AWS Quickstart](https://aws-quickstart.github.io/quickstart-amazon-selling-partner-api)** — AWS reference architecture.
- **[amzn/selling-partner-api-samples](https://github.com/amzn/selling-partner-api-samples)** *(reference for context)* — official code samples.

---

## 11. Workflow Recipes

These are **not tools** — they're 10-line patterns showing how to compose the above.

### Recipe A — Amazon Competitor Price Alert

```
cron (every 6h)
    └──► omerhalid/Amazon-Price-Tracker (or your own scrape loop)
              │
              ├──► parse price
              ├──► if delta > 5% from last seen:
              │       └──► Telegram / Email alert
              └──► write to SQLite for charting
```

**Stack**: 1 scraper + 1 cron + 1 alert channel. ~50 lines of glue.

### Recipe B — New-Review Notification

```
cron (every 2h)
    └──► scrapehero-code/amazon-review-scraper (or oxylabs)
              │
              ├──► diff vs last seen (changedetection.io-style)
              ├──► VADER sentiment on new reviews
              ├──► if sentiment < -0.3:
              │       └──► Slack #alerts-low-rating
              └──► archive to CSV
```

**Stack**: scraper + VADER + alert. ~30 lines.

### Recipe C — Shopify Low-Stock Alert

```
Shopify webhook (inventory_levels/update)
    └──► your server (Cloudflare Worker / FastAPI)
              │
              ├──► if available < threshold:
              │       └──► Telegram / Slack alert
              └──► optionally: write to Supabase for dashboard
```

**Stack**: 1 webhook + 1 worker. ~40 lines.

### Recipe D — Listing Copy Rewrite (Local LLM)

```
input: competitor product URL + my current title
    │
    ▼
Jina Reader (or ScrapeGraphAI) → competitor description
    │
    ▼
Ollama (qwen2.5 / llama3) with prompt:
    "Rewrite this title in < 200 chars, including keywords A, B, C.
     Match my brand voice. Don't invent claims."
    │
    ▼
output: rewritten title + bullets
```

**Stack**: 1 scraper + 1 LLM call. No SaaS, no data leaves your machine.

### Recipe E — Telegram Shop in a Day

```
git clone ilyarolf/AiogramShopBot
    │
    ├──► edit .env: bot token, payment keys
    ├──► docker-compose up -d
    └──► /start  → you're selling
```

**Stack**: clone, env, up. Zero code for an MVP.

### Recipe F — Privacy-Friendly Storefront Analytics

```
Plausible CE  (or Umami)
    │
    ├──► drop script tag in Shopify theme.liquid
    ├──► custom events: add_to_cart, checkout_started
    └──► dashboard: conversion funnel, top products
```

**Stack**: 1 docker container + 1 script tag.

### Recipe G — Cross-Marketplace Price Map

```
list of my SKUs
    │
    ▼
for each SKU:
    ├──► oxylabs/amazon-scraper
    ├──► omkarcloud/aliexpress-scraper
    ├──► Jina Reader on a Taobao / 1688 URL
    ├──► normalize: {sku, source, price, currency, in_stock}
    └──► write to Supabase / Airtable / Notion
```

**Stack**: 3 small scrapers + 1 sink. ~80 lines.

### Recipe H — Multi-Channel Review Triage

```
Shopify reviews + Amazon reviews + Trustpilot reviews
    │
    ▼
spaCy (NER) + BERTopic (themes)
    │
    ├──► cluster: "sizing", "shipping", "defect", "love", "..."
    ├──► sentiment per cluster
    ├──► if new defect theme emerges:
    │       └──► Slack #product-alerts
    └──► weekly digest: top 5 themes with example quotes
```

**Stack**: 1 collector script + spaCy + BERTopic + Slack. ~120 lines.

---

## Contributing

Contributions welcome. Read [CONTRIBUTING.md](CONTRIBUTING.md).

Hard rules:

1. **One job per tool.** If a project has more than ~3 major capabilities, it's a platform — reject.
2. **Stars ≥ 200** OR it fills a unique gap with a working example (explain why in PR).
3. **Commits within 12 months** OR explicitly archived-mature.
4. **Direct retail/ecommerce relevance.** Generic dev tooling, generic LLM engines, generic BI — reject.
5. **No SaaS-only entries** unless marked as "context" (we list them so people know what to replace, not to use).

---

## License

[CC0 1.0](http://creativecommons.org/publicdomain/zero/1.0/) — public domain.
