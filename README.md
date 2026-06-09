# Awesome E-commerce & Retail: AI Workflows & Small Tools

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: CC0-1.0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](http://creativecommons.org/publicdomain/zero/1.0/)

A curated list of **AI workflow platforms** and **small open-source tools** for e-commerce and retail — built for the people who actually run stores, not the ones building them from scratch.

> **Scope**: AI workflow / agent builders (n8n, Dify, Coze, Flowise, Langflow, bolt.new, etc.) — both the platforms themselves and the small open-source tools that plug into them. Covers pricing, listings, reviews, support, marketing, ops.

> **Out of scope**: Big monolithic commerce platforms (Medusa, Saleor, Shopware, ERPNext). Those are well-served by `olivrg/Awesome-Open-Source-eCommerce-Platforms` and `notrab/awesome-headless-commerce`. We're the other side of the line: **AI-powered productivity for everyone running a store**, not the platform vendors themselves.

---

## Table of Contents

1. [How to Choose (Decision Matrix)](#how-to-choose-decision-matrix)
2. [AI Workflow & Agent Builders](#1-ai-workflow--agent-builders)
3. [Template & Workflow Libraries](#2-template--workflow-libraries)
4. [Scraping, Pricing & Competitor Intel](#3-scraping-pricing--competitor-intel)
5. [Listings, Copy & SEO](#4-listings-copy--seo)
6. [Reviews, Sentiment & Customer Insight](#5-reviews-sentiment--customer-insight)
7. [Customer Support AI](#6-customer-support-ai)
8. [Marketing Automation & Ads](#7-marketing-automation--ads)
9. [Image, Video & Creative](#8-image-video--creative)
10. [Voice, Chat & Live Ops](#9-voice-chat--live-ops)
11. [Local LLM & Self-host Stacks](#10-local-llm--self-host-stacks)
12. [End-to-End Workflow Patterns](#11-end-to-end-workflow-patterns)
13. [Contributing](#contributing)

---

## How to Choose (Decision Matrix)

| If you want to… | Pick | Why |
|---|---|---|
| Drag-drop a no-code workflow, lots of integrations | **n8n** | 400+ integrations, fair-code (Sustainable Use License), self-host |
| Build RAG + agents with first-class Knowledge base | **Dify** | Explicit "Knowledge" surface, app + workflow builder, plugins |
| Visual LLM canvas, both Python and TypeScript SDKs | **Flowise** | 100+ LLMs, MCP support, full programmatic access |
| Build fully in TypeScript in the browser | **bolt.new / bolt.diy** | Instant app from prompt, full-stack code ownership |
| Visual flow programming for RAG / multi-agent | **Langflow** | DataStax-backed, drag-drop LLM orchestration |
| ByteDance ecosystem, agent platforms with eval | **Coze Studio + Coze Loop** | Visual agent dev + production monitoring/eval |
| Build one-off workflows in plain text YAML | **AnythingLLM** or **Activepieces** | Lightweight, single-user, fast to deploy |
| Wire workflows into Notion/Sheets/Airtable without code | **Activepieces** or **n8n** | Best UX for non-dev teams |

> **Rule of thumb**: start with n8n for general automation + LLM mix. Switch to Dify if your main job is RAG/agents. Use Flowise/Langflow if you're a developer who wants Python/TS SDKs. Use Coze if you want a managed "agent platform" experience with eval and observability.

---

## 1. AI Workflow & Agent Builders

The platforms where you compose prompts, tools, and integrations into usable flows.

### Visual / No-code / Low-code

- **[n8n](https://github.com/n8n-io/n8n)** — Fair-code workflow automation with native AI nodes (400+ integrations, 100k+ community nodes). Self-host or cloud. Use when: you want Zapier-grade UX with full LLM and code-node escape hatches. *License: Sustainable Use License (not OSI-open; check for SaaS restrictions).*
- **[Dify](https://github.com/langgenius/dify)** — Visual LLM app + agent + workflow builder, 100k+ stars. First-class RAG "Knowledge" base, plugin marketplace, model agnostic. Apache-2.0 with extra conditions. Use when: you ship a RAG or agent product and want versioned flows, evals, and observability.
- **[Coze Studio](https://github.com/coze-dev/coze-studio)** — ByteDance's visual AI agent platform, open-sourced core. Chatbots, workflows, plugins, multi-channel publishing. Apache-2.0. Use when: you want the same engine as the commercial Coze platform.
- **[Coze Loop](https://github.com/coze-dev/coze-loop)** — Companion to Coze Studio: prompt engineering, evaluation, monitoring, optimization. Apache-2.0. Use when: you ship Coze agents and need to track and improve them in production.
- **[Flowise](https://github.com/FlowiseAI/Flowise)** — Drag-drop LLM / agent / chatflow builder, 100+ integrations, MCP support, TypeScript + Python SDKs. Apache-2.0. Use when: you want a canvas plus code-level SDKs (good for embedding in real apps).
- **[Langflow](https://github.com/langflow-ai/langflow)** — Python/React visual framework for multi-agent + RAG, MIT. DataStax-backed. Use when: you want LangChain-style power without writing LangChain.
- **[bolt.diy](https://github.com/stackblitz-labs/bolt.diy)** — Open-source full-stack app builder in the browser. Prompt → Next.js / Vite / Svelte app, LLM-agnostic. MIT. Use when: you want to ship a custom store/admin tool from a prompt in minutes.
- **[AnythingLLM](https://github.com/Mintplex-Labs/anything-llm)** — All-in-one desktop + Docker LLM app, RAG, agents, multi-user. MIT. Use when: you want a single-user "ChatGPT-with-your-data" with workflow side.
- **[Activepieces](https://github.com/activepieces/activepieces)** — Open-source Zapier alternative, 280+ integrations, AI-friendly. MIT. Use when: you want a clean modern UI and friendlier licensing than n8n.
- **[Sim](https://github.com/simstudioai/sim)** — Visual AI agent workflow builder with first-class tool integrations, MIT. Use when: you want something newer with a tighter DX than n8n.
- **[ToolJet](https://github.com/ToolJet/ToolJet)** — Open-source low-code platform with AI agents built in. AGPL-3.0. Use when: you want internal tools + workflows on one canvas.
- **[Rowy](https://github.com/rowy-hq/rowy)** — Airtable-like UI on top of Firestore + cloud functions + AI prompts. Apache-2.0. Use when: you live in spreadsheets but want a backend.

### Code-first / SDK-first

- **[LangChain](https://github.com/langchain-ai/langchain)** — Python + JS LLM orchestration. MIT. The reference agent framework.
- **[LlamaIndex](https://github.com/run-llama/llama_index)** — Data framework for LLM apps, MIT. Best for RAG-heavy workloads.
- **[CrewAI](https://github.com/crewAIInc/crewAI)** — Multi-agent orchestration with role-based crews, MIT.
- **[AutoGen](https://github.com/microsoft/autogen)** — Microsoft Research multi-agent framework, MIT. Conversation-pattern agents.
- **[Agno (ex-Phidata)](https://github.com/agno-agi/agno)** — AgentOS, fastest-growing Python agent framework, MIT.
- **[Haystack](https://github.com/deepset-ai/haystack)** — Deepset's pipelines for production RAG + agents, Apache-2.0.
- **[Semantic Kernel](https://github.com/microsoft/semantic-kernel)** — Microsoft's SDK for AI orchestration, MIT.
- **[Letta](https://github.com/letta-ai/letta)** — Stateful agents with long-term memory, Apache-2.0.
- **[PocketFlow](https://github.com/The-Pocket/PocketFlow)** — Minimal 100-line LLM framework, MIT. Use when: you hate frameworks.

---

## 2. Template & Workflow Libraries

Pre-built flows you can fork. Don't reinvent the prompt.

- **[awesome-n8n-templates](https://github.com/enescingoz/awesome-n8n-templates)** — 280+ free ready-to-import n8n workflows (Gmail, Telegram, OpenAI, WhatsApp, Slack, WordPress, Sheets, Discord). Use when: you need a working n8n flow for a common task.
- **[awesome-n8n (community nodes)](https://github.com/restyler/awesome-n8n)** — Top 100 n8n community nodes by monthly npm downloads. Use when: you need a connector n8n doesn't ship with.
- **[n8n-workflows (zie619)](https://github.com/zie619/n8n-workflows)** — 4,300+ n8n workflow JSONs, the largest scraped collection. Use when: you want raw templates to mine, not curated ones.
- **[dify-workflow](https://github.com/topics/dify-workflow)** — GitHub topic for Dify DSL templates (.yml). Use when: you want chatflows/agent flows to import.
- **[Flowise templates](https://github.com/FlowiseAI/Flowise/tree/main/marketplace)** — Official Flowise marketplace templates.
- **[Langflow templates](https://github.com/langflow-ai/langflow_examples)** — Langflow example projects.
- **[n8n AI Starter Kit](https://github.com/n8n-io/ai-starter-kit)** — Official n8n starter for AI + vector store + chat.

---

## 3. Scraping, Pricing & Competitor Intel

The "what's everyone else doing" stack.

- **[Firecrawl](https://github.com/mendableai/firecrawl)** — API + open-source scraper that turns any site into clean markdown/JSON for LLMs. AGPL-3.0. Use when: you need to feed clean web data to a RAG pipeline or AI agent.
- **[Crawl4AI](https://github.com/unclecode/crawl4ai)** — Open-source async web crawler purpose-built for LLM ingestion. Apache-2.0. Use when: you want a self-host Firecrawl.
- **[ScrapeGraphAI](https://github.com/ScrapeGraphAI/ScrapeGraphAI)** — LLM-driven scraper that uses LLMs to extract structured data from pages. MIT. Use when: you need "extract the price + SKU + stock" with one prompt.
- **[dataprice](https://github.com/Glitchero/dataprice)** — Open-source competitor price tracker (Python). Use when: you want a self-host price-monitoring engine for your category.
- **[oxylabs/ecommerce-category-scraper](https://github.com/oxylabs/ecommerce-category-scraper)** — AI-powered category & price scraping templates. Apache-2.0. Use when: you need production-grade scraper boilerplate.
- **[AutoScraper](https://github.com/alirezamika/autoscraper)** — Learn-to-scrape with a few examples, no rules needed. MIT. Use when: you need quick, light scraping without LLM.
- **[Crawlee](https://github.com/apify/crawlee)** — Node.js / Python web scraping + browser automation library. Apache-2.0. Use when: you're building a serious scraper, not a one-off.
- **[Browse AI](https://github.com/browse-ai/browseai-cli)** — CLI companion to Browse AI platform, MIT. Use when: you want to record a "robot" scraping a competitor site and replay it on a schedule.

---

## 4. Listings, Copy & SEO

Optimize product pages, titles, descriptions, meta.

- **[Listing AI / Helium10-style open tools]** — *(this category is SaaS-heavy; we list open-source options only)*
- **[Jina Reader](https://github.com/jina-ai/reader)** — API that converts any URL to clean LLM-friendly text. Apache-2.0. Use when: you want to feed any product page into a prompt for rewriting.
- **[MarkItDown](https://github.com/microsoft/markitdown)** — Microsoft tool to convert any file (PDF, DOCX, HTML, images) to Markdown for LLM ingestion. MIT. Use when: you need to turn supplier catalogs or PDFs into LLM-ready text.
- **[Surya](https://github.com/VikParuchuri/surya)** — OCR for 90+ languages, layout-aware. GPL-3.0. Use when: you need to extract text from product images, screenshots, or supplier scans.
- **[Marker](https://github.com/datalab-to/marker)** — Fast PDF/image → Markdown converter, Apache-2.0. Use when: you want to convert product spec PDFs into structured data.
- **[PaddleOCR](https://github.com/PaddlePaddle/PaddleOCR)** — Baidu's multilingual OCR, Apache-2.0. Use when: you need to read text from product photos at scale.
- **[MoneyPrinterTurbo](https://github.com/harry0703/MoneyPrinterTurbo)** — One-click short video generator from a topic. Apache-2.0. Use when: you want to auto-generate product promo videos for social.
- **[VideoLingo](https://github.com/HKUDS/VideoLingo)** — Auto-dub, subtitle, translate videos. Apache-2.0. Use when: you localize product video for multiple markets.
- **[LlamaParse](https://github.com/run-llama/llama_parse)** *(closed, but the open-source parsers above are alternatives)* — *(referenced for context, not included)*

---

## 5. Reviews, Sentiment & Customer Insight

Mine reviews and feedback for product / ops decisions.

- **[VADER](https://github.com/cjhutto/vaderSentiment)** — Rule-based sentiment tuned for social/review text. MIT. Use when: you want a no-LLM, no-GPU sentiment engine.
- **[TextBlob](https://github.com/sloria/TextBlob)** — Simple Python NLP for sentiment, noun-phrase extraction, translation. MIT. Use when: you need a quick sentiment check on a CSV of reviews.
- **[spaCy](https://github.com/explosion/spaCy)** — Industrial-strength NLP with sentiment, NER, embeddings. MIT. Use when: you need to build a real review-mining pipeline.
- **[BERTopic](https://github.com/MaartenGr/BERTopic)** — Topic modeling using transformers + c-TF-IDF, MIT. Use when: you want to cluster 100k reviews into themes ("sizing issues", "battery life").
- **[Vespper](https://github.com/vespper/vespper)** — LLM-based observability copilot. MIT. Use when: you want an AI to explain what's broken from logs/metrics.
- **[Argilla](https://github.com/argilla-io/argilla)** — Open-source data labeling + curation for LLMs. Apache-2.0. Use when: you build review datasets for fine-tuning or eval.
- **[Cleanlab](https://github.com/cleanlab/cleanlab)** — Data-centric AI for finding label issues, MIT. Use when: you have a tagged review dataset and want to find mislabels.

---

## 6. Customer Support AI

Answer tickets, summarize convos, train on your data.

- **[Chatwoot](https://github.com/chatwoot/chatwoot)** — Omnichannel support inbox, MIT, with built-in AI agent ("Captain"). Use when: you want to self-host Intercom + LLM.
- **[Rasa](https://github.com/RasaHQ/rasa)** — Open-source conversational AI / chatbots, Apache-2.0. Use when: you need full control over the NLU + dialogue.
- **[Botpress](https://github.com/botpress/botpress)** — Visual chatbot builder with LLM and NLU, MIT. Use when: you want a self-host ManyChat with real NLU.
- **[Typebot](https://github.com/baptisteArno/typebot)** — Visual conversational form builder, AGPL-3.0 with cloud option. Use when: you want to build lead-gen / survey / support flows that look like chat.
- **[Quivr](https://github.com/QuivrHQ/quivr)** — "Second brain" over your docs and past tickets. Apache-2.0. Use when: you want an internal RAG that knows your store's policies + past support.
- **[Paperless-AI](https://github.com/clusterzx/paperless-ai)** — Auto-tag, summarize, and chat with Paperless-ngx docs. MIT. Use when: you auto-import invoices and want them summarized.

---

## 7. Marketing Automation & Ads

Email, SMS, social, ads — at AI speed.

- **[Mautic](https://github.com/mautic/mautic)** — Full marketing automation (email, SMS, social, segments, campaigns). GPL-3.0. Use when: you want a self-host HubSpot.
- **[Listmonk](https://github.com/knadh/listmonk)** — High-performance newsletter + mailing list manager, AGPL-3.0. Use when: your only job is sending newsletters fast.
- **[Postal](https://github.com/postalserver/postal)** — Open-source mail server for transactional + bulk email. MIT. Use when: you self-host all your email.
- **[Lemlist / Instantly alternatives]** — *(SaaS-only; nothing open-source to recommend here.)*
- **[Open Web Analytics](https://github.com/OpenWebAnalytics/openwebanalytics)** — Self-host web analytics, GPL-2.0. Use when: you want Plausible / GA behavior without SaaS.
- **[Plausible Analytics (Community Edition)](https://github.com/plausible/community-edition)** — Privacy-friendly analytics, AGPL-3.0. Use when: you need cookieless analytics with no GDPR dance.
- **[Umami](https://github.com/umami-software/umami)** — Fast, privacy-friendly analytics, MIT. Use when: you want Plausible but lighter.
- **[PostHog (OSS)](https://github.com/PostHog/posthog)** — Product analytics + session replay + feature flags, MIT. Use when: you want GA + Mixpanel + Hotjar in one self-host stack.
- **[Chatwoot (also in §6)](https://github.com/chatwoot/chatwoot)** — Its broadcast / campaigns module can drive marketing conversations.
- **[Ghostwriter-LLM](https://github.com/robgraham/ghostwriter-llm)** — WordPress content generator using your brand voice. MIT. Use when: you blog from WP and want AI drafts.

---

## 8. Image, Video & Creative

Product photos, ads, social.

- **[ComfyUI](https://github.com/comfyanonymous/ComfyUI)** — Node-based Stable Diffusion UI, MIT. Use when: you want full control over image generation pipelines (virtual try-on, background swap, etc.).
- **[Stable Diffusion WebUI (A1111)](https://github.com/AUTOMATIC1111/stable-diffusion-webui)** — The reference SD UI, MIT. Use when: you want to run SD locally for product imagery.
- **[InvokeAI](https://github.com/invoke-ai/InvokeAI)** — Polished SD-based creative engine, Apache-2.0. Use when: you want a professional creative canvas, not a power-user one.
- **[Fooocus](https://github.com/lllyasviel/Fooocus)** — Minimal SD XL UI, MIT. Use when: you want Midjourney-grade simplicity, self-host.
- **[Open-LLM-VTuber](https://github.com/Open-LLM-VTuber/Open-LLM-VTuber)** — Live2D + LLM + voice VTuber. MIT. Use when: you want a streaming AI avatar for live commerce.
- **[MoneyPrinterTurbo](https://github.com/harry0703/MoneyPrinterTurbo)** — One-click short video from a topic, Apache-2.0. *(also in §4)*
- **[Submaker / autosub](https://github.com/agermanidis/autosub)** — Auto subtitle generator. MIT. Use when: you caption product videos.
- **[Streamlit / Gradio]** — *(not creative, but: use to build quick visual tools around any of the above.)*

---

## 9. Voice, Chat & Live Ops

Phone, voice, live chat, transcription.

- **[Rasa](https://github.com/RasaHQ/rasa)** — *(also in §6)* Use when: you want a voice + chat bot with NLU.
- **[Whisper (openai-whisper)](https://github.com/openai/whisper)** — OpenAI's speech-to-text, MIT. Use when: you transcribe customer calls, voicemails, video reviews.
- **[WhisperX](https://github.com/m-bain/whisperX)** — Faster Whisper with word-level timestamps, BSD-4. Use when: you need to align transcript with audio for QA.
- **[Faster-Whisper](https://github.com/SYSTRAN/faster-whisper)** — CTranslate2 port of Whisper, 4x faster, MIT. Use when: you need real-time transcription on commodity GPUs.
- **[Piper](https://github.com/rhasspy/piper)** — Fast local neural TTS, MIT. Use when: you need on-device voice for IVR / virtual try-on.
- **[Coqui TTS](https://github.com/coqui-ai/TTS)](https://github.com/coqui-ai/TTS) — Library for advanced TTS, MPL-2.0. Use when: you need multilingual, voice-cloned TTS.
- **[ChatterBot](https://github.com/gunthercox/ChatterBot)** — Python conversational engine, BSD-3. Use when: you need a quick no-LLM chatbot for FAQs.
- **[Rocket.Chat](https://github.com/RocketChat/RocketChat)** — Omnichannel chat platform, MIT. Use when: you want a self-host Slack/Teams with a customer-chat bridge.

---

## 10. Local LLM & Self-host Stacks

The bedrock. Run models on your hardware.

- **[Ollama](https://github.com/ollama/ollama)** — Run Llama / Mistral / Phi / Qwen locally with one command. MIT. The default.
- **[LM Studio](https://github.com/lmstudio-ai/lmstudio)** — Desktop app for running local LLMs. MIT. *(closed binary builds; open-source core.)*
- **[vLLM](https://github.com/vllm-project/vllm)** — High-throughput LLM serving, Apache-2.0. Use when: you serve an in-house model for production.
- **[llama.cpp](https://github.com/ggerganov/llama.cpp)** — C++ inference for Llama-family models, MIT. Use when: you have edge / ARM / weird hardware.
- **[LocalAI](https://github.com/mudler/LocalAI)** — OpenAI-compatible local inference, MIT. Use when: you want to swap OpenAI for self-host without code changes.
- **[text-generation-inference (TGI)](https://github.com/huggingface/text-generation-inference)** — HF's Rust-based server, Apache-2.0. Use when: you need HF model serving at scale.
- **[Open WebUI](https://github.com/open-webui/open-webui)** — Polished chat UI for local LLMs, MIT. Use when: you want ChatGPT UX on your own hardware.
- **[KoboldCpp / KoboldAI](https://github.com/LostRuins/koboldcpp)** — Local creative-writing + roleplay UI, AGPL-3.0. Use when: you want local LLM for copy generation.
- **[GPTCache](https://github.com/zilliztech/GPTCache)** — Semantic cache for LLM queries, Apache-2.0. Use when: you want to cut LLM cost on repeated queries (FAQ, similar reviews).

### Vector Databases

- **[Chroma](https://github.com/chroma-core/chroma)** — Embedding DB, Apache-2.0. Default for small RAG.
- **[Qdrant](https://github.com/qdrant/qdrant)** — Rust vector search, Apache-2.0. Use when: production RAG at scale.
- **[Milvus](https://github.com/milvus-io/milvus)** — Distributed vector DB, Apache-2.0. Use when: billion-scale vectors.
- **[Weaviate](https://github.com/weaviate/weaviate)** — Vector + hybrid search, BSD-3. Use when: you want a turnkey vector + filtering combo.
- **[LanceDB](https://github.com/lancedb/lance)** — Embedded columnar + vector DB, Apache-2.0. Use when: you want DuckDB-style local + vectors.
- **[pgvector](https://github.com/pgvector/pgvector)** — Postgres extension, PostgreSQL License. Use when: you already have Postgres.

---

## 11. End-to-End Workflow Patterns

These aren't tools — they're **recipes** that show how the pieces fit.

### Pattern A — Competitor Price Monitor (n8n + Firecrawl + Supabase)

```
Schedule (every 6h) ──► n8n
                          │
                          ├──► Firecrawl / ScrapeGraphAI: fetch competitor product page
                          ├──► LLM node: extract {price, sku, in_stock}
                          ├──► Supabase: upsert into `competitor_prices` table
                          ├──► Compare with my_price
                          ├──► If delta > 5% → Slack alert
                          └──► Metabase dashboard
```

**What you get**: real-time competitor intel without manual checks. Total stack is MIT / Apache.

### Pattern B — AI Customer Support Agent (Dify / Coze + RAG)

```
Customer question
    │
    ▼
Dify / Coze chatflow
    │
    ├──► RAG over: my product catalog, FAQ, return policy, past tickets
    ├──► LLM (gpt-4o-mini / qwen / deepseek) drafts answer
    ├──► Guardrail: if confidence < 0.7 → handoff to human
    ├──► If returns question → call Shopify / Order API to look up order
    └──► Send via Chatwoot / email
```

**What you get**: 60-80% auto-resolution of tier-1 questions, no SaaS lock-in.

### Pattern C — Product Listing Optimizer (Flowise + Scraper + LLM)

```
List of my SKUs
    │
    ▼
For each SKU:
    ├──► Scraper: fetch top-10 search results
    ├──► LLM: analyze common attributes / claims / keywords
    ├──► LLM: rewrite my title + bullet points + description
    ├──► LLM: suggest SEO meta + alt text
    └──► Push to Shopify / Amazon SP-API
```

**What you get**: data-driven listing copy, not vibes.

### Pattern D — Review Triage Pipeline (n8n + spaCy / BERTopic + Slack)

```
Daily scrape of new reviews
    │
    ▼
n8n
    ├──► spaCy / VADER: sentiment score
    ├──► BERTopic: cluster by theme
    ├──► If sentiment < -0.5 OR theme in {defect, sizing, shipping} → Slack alert
    ├──► If theme is new → log for product team
    └──► Weekly digest email to ops
```

**What you get**: catch a 1-star wave the same day, not the same week.

### Pattern E — Live Commerce Avatar (Ollama + Piper + ComfyUI + OBS)

```
Voice from streamer ──► Whisper (transcribe)
                              │
                              ▼
                    LLM (qwen / llama local) — answer draft
                              │
                              ▼
                    Piper TTS (voice)
                              │
                              ▼
              ComfyUI: live2d / portrait avatar
                              │
                              ▼
                         OBS → Twitch / TikTok Live
```

**What you get**: 24/7 AI streamer for low-cost live commerce.

### Pattern F — Self-host RAG for Storefront Q&A (AnythingLLM + Ollama + pgvector)

```
Shopify / WooCommerce customer types question in chat widget
    │
    ▼
n8n webhook
    │
    ├──► AnythingLLM workspace (RAG over my products + FAQ)
    ├──► Ollama local LLM (qwen2.5, no data leaves my server)
    ├──► pgvector on my Postgres
    └──► Reply via Chatwoot widget
```

**What you get**: a chat that knows your store, with no SaaS and no data leakage.

---

## Contributing

Contributions welcome. Read [CONTRIBUTING.md](CONTRIBUTING.md) for the hard rules.

TL;DR:

1. Project must be open source with a license in the repo.
2. Stars ≥ 500 OR it fills a unique gap (explain why).
3. Commits within the last 12 months OR explicitly archived/mature.
4. Direct relevance to **AI workflow** OR **small tool used in e-commerce/retail ops**.
5. Don't propose a 40k-star SaaS — we already know about them. We want the long tail.

---

## License

[CC0 1.0](http://creativecommons.org/publicdomain/zero/1.0/) — public domain.
