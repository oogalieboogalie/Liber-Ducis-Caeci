<div align="center">

<img src="./assets/hero_banner.png" alt="A curious figure stepping into a luminous network of automation workflows" width="100%"/>

# Liber Ducis Caeci

### *The Book of the Blind Leader*

**A curated library of n8n workflow templates — AI agents, automation suites, RAG pipelines, and more.**

[![n8n](https://img.shields.io/badge/n8n-workflow%20automation-FF6D5A?style=for-the-badge&logo=n8n&logoColor=white)](https://n8n.io)
[![AI Powered](https://img.shields.io/badge/AI-Powered-412991?style=for-the-badge&logo=openai&logoColor=white)](https://openai.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](./LICENSE)

---

*They say the blind can't lead the blind. But I can lead the way.*

---

</div>

## 📚 What Is This?

A growing collection of production-grade n8n workflows organized into themed collections. Each workflow is importable, documented, and built with real-world automation patterns — AI-powered data extraction, smart routing, vector-based learning, and full audit trails.

Whether you're automating bookkeeping, building AI agent systems, or setting up knowledge pipelines — grab what you need.

---

## 🗂️ Collections

### ⚡ [QB Autopilot Suite](./QB_Autopilot_Suite/)
> *Complete QuickBooks automation ecosystem — 4 interconnected workflows*

| Workflow | What It Does |
|:---------|:-------------|
| Client Onboarding Orchestrator | Form → AI profiling → QB customer creation → CRM → welcome email → kickoff meeting |
| Invoice Processing Hub | Invoice intake → AI extraction (GPT-4o-mini) → validation → QB bill posting |
| Expense Automation Engine | Receipt capture → AI analysis → smart categorization → auto-approve → QB posting |
| Master Control Dashboard | Health monitoring → daily reports → alerting → Notion logging |

**Integrations:** QuickBooks Online, OpenAI, Notion, Gmail, Google Calendar, Google Drive, Qdrant

📖 [Full docs & setup guide →](./QB_Autopilot_Suite/README.md)

---

### 🧠 ExoCortex Command Center
> *AI-powered central nervous system for orchestrating multiple agent workflows*

| Workflow | Description |
|:---------|:------------|
| `exocortex_command_center.json` | Full command center with webhook routing, agent dispatch, and response handling |
| `exocortex_command_center_v2.json` | V2 with improvements |
| `exocortex_command_center_complete.json` | Complete standalone version |
| `exocortex_routing_only.json` | Lightweight — routing logic only |
| `exocortex_ultra_simple.json` | Minimal proof-of-concept |
| `exocortex_piece1-4` | Modular breakdown (webhook routing, agent execution, logging, response) |

---

### 🤖 AI Agents
> *Standalone AI agents for specific business functions*

| Workflow | What It Does |
|:---------|:-------------|
| `censai_research_agent.json` | Web search & data extraction agent via Tavily |
| `content_pipeline_agent.json` | Video processing → AI analysis → multi-platform social distribution |
| `client_management_agent.json` | Client relationship management automation |
| `analytics_agent.json` | Business analytics and reporting agent |
| `monitoring_agent.json` | System monitoring and alerting |

---

### 📖 RAG & Knowledge Systems
> *Retrieval-Augmented Generation pipelines and knowledge base management*

| Workflow | What It Does |
|:---------|:-------------|
| `mvrag_ingest_cohere_supabase.json` | Document ingestion with Cohere embeddings → Supabase vector store |
| `mvrag_ask_local_llm.json` | Query pipeline — ask questions against your knowledge base via local LLM |
| `mvrag_query_only.json` | Lightweight query-only RAG endpoint |
| `contextual_retrieval.json` | Context-aware document retrieval |
| `family_brain_architecture.json` | Multi-user knowledge brain architecture |
| `family_brain_ingestion_fixed.json` | Knowledge ingestion pipeline |
| `family_brain_query_system.json` | Natural language query system |
| `family_brain_supabase_schema.sql` | Database schema for the brain system |
| `business_brain_ingestion_improved.json` | Business-focused knowledge ingestion |

---

### 🔍 Job Search Automation
> *Automated job crawling, filtering, and tracking*

| Workflow | What It Does |
|:---------|:-------------|
| `JobCrawler_V1.json` | Apify-powered job scraping → remote filter → date filter → Google Sheets logging |
| `JobCrawler Digest.json` | Digest/summary version of crawled job results |

---

### 🏗️ Architect Workflows
> *Meta-workflows for building and managing other workflows*

| Workflow | What It Does |
|:---------|:-------------|
| `architect-improved-workflow.json` | AI-assisted workflow design and generation |
| `architect-local-memory-system.json` | Local memory/context system for persistent AI agents |
| `architect-webhook-chat.json` | Webhook-based conversational interface |

---

### 🛠️ Utilities & Standalone
> *Single-purpose workflows and helpers*

| Workflow | What It Does |
|:---------|:-------------|
| `irs_call_assistant.json` | Strategic IRS call window alerts (7:05 AM / 4:30 PM weekdays) |
| `capture_webhook.json` | Generic webhook capture utility |
| `n8n_Calendar_Sync.json` | Calendar synchronization |
| `n8n_Idea_Enrichment.json` | Idea capture and enrichment pipeline |
| `n8n_Weekly_Summary_Email.json` | Weekly digest email automation |
| `client_onboarding_pipeline.json` | Generic client onboarding (non-QB version) |

---

## 🚀 Getting Started

### Import Any Workflow

1. Open your n8n instance
2. **Add Workflow** → **Import from File**
3. Select any `.json` file from this repo
4. Configure credentials for the services it uses
5. Activate

### For Full Collections (like QB Autopilot Suite)

Each collection folder has its own `README.md`, `SETUP.md`, and `CREDENTIALS.md` with detailed instructions.

---

## 📁 Repo Structure

```
Liber-Ducis-Caeci/
├── assets/                          # Images and media
│   └── hero_banner.png
├── QB_Autopilot_Suite/              # 🏦 QuickBooks automation collection
│   ├── 01-04 workflow JSONs
│   ├── README.md
│   ├── SETUP.md
│   └── CREDENTIALS.md
├── [standalone workflows].json      # Individual importable workflows
├── README.md                        # You are here
└── LICENSE
```

---

## 🤝 Contributing

Found a bug? Built something cool? PRs welcome.

1. Fork the repo
2. Create your branch (`git checkout -b feature/new-workflow`)
3. Add your workflow + a brief description
4. Open a Pull Request

---

## 📄 License

MIT — Use freely, modify as needed. See [LICENSE](./LICENSE).

---

<div align="center">

**Built with 🤖 + ☕ by [oogalieboogalie](https://github.com/oogalieboogalie)**

*a me, ad te.*

</div>
