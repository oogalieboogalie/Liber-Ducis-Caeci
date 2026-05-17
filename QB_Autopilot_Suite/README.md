<div align="center">

# ⚡ QB Autopilot Suite

### AI-Powered QuickBooks Automation for n8n

[![n8n](https://img.shields.io/badge/n8n-workflow%20automation-FF6D5A?style=for-the-badge&logo=n8n&logoColor=white)](https://n8n.io)
[![QuickBooks](https://img.shields.io/badge/QuickBooks-Online-2CA01C?style=for-the-badge&logo=intuit&logoColor=white)](https://quickbooks.intuit.com)
[![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4o--mini-412991?style=for-the-badge&logo=openai&logoColor=white)](https://openai.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](./LICENSE)

**4 production-ready n8n workflows that automate bookkeeping end-to-end.**<br/>
From client onboarding to invoice processing, expense categorization, and operations monitoring.

---

</div>

## 📦 What's Inside

| # | Workflow | What It Does |
|:--|:---------|:-------------|
| 01 | **Client Onboarding Orchestrator** | Form → AI profiling → QB customer creation → CRM record → welcome email → kickoff meeting |
| 02 | **Invoice Processing Hub** | Invoice intake → AI extraction (GPT-4o-mini) → validation → QB bill posting → confidence-gated human review |
| 03 | **Expense Automation Engine** | Receipt capture → AI analysis → smart categorization w/ vector learning → auto-approve → QB posting → Drive archive |
| 04 | **Master Control Dashboard** | 15-min health checks → daily executive reports → Notion logging → alerting |

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────┐
│         04. Master Control Dashboard        │
│        (Health Checks / Daily Reports)      │
└────────┬──────────────┬─────────────────────┘
         │              │  monitors
    ┌────▼────┐   ┌─────▼──────┐   ┌──────────────┐
    │   02.   │   │    03.     │   │     01.      │
    │ Invoice │   │  Expense   │   │  Onboarding  │
    │   Hub   │   │  Engine    │   │ Orchestrator │
    └────┬────┘   └─────┬──────┘   └──────┬───────┘
         │              │                  │
         ▼              ▼                  ▼
    ┌─────────────────────────────────────────┐
    │           QuickBooks Online API          │
    │      (Bills, Expenses, Customers)       │
    └─────────────────────────────────────────┘
```

---

## ✨ Key Features

| Feature | Details |
|:--------|:--------|
| 🤖 **AI Data Extraction** | GPT-4o-mini reads invoices/receipts → structured JSON |
| 🎯 **Confidence Gating** | High confidence = auto-post. Low confidence = human review |
| 🧠 **Smart Categorization** | Qdrant vector store learns from past expense categorizations |
| ✅ **Auto-Approval Rules** | Expenses <$100 + >85% confidence = auto-post to QB |
| 🏭 **Industry-Specific Setup** | Onboarding generates Chart of Accounts by industry |
| 📋 **Table of Truth Pattern** | Centralized Set node normalizes data in every workflow |
| 📝 **Full Audit Trail** | Every action logged to Notion databases |

---

## 🚀 Quick Start

### 1. Clone
```bash
git clone https://github.com/YOUR_USERNAME/qb-autopilot-suite.git
```

### 2. Import into n8n
Import the 4 JSON files in order (01 → 04):
- n8n → **Add Workflow** → **Import from File**

### 3. Configure
- Set up credentials → [CREDENTIALS.md](./CREDENTIALS.md)
- Create Notion databases → [SETUP.md](./SETUP.md)
- Replace all `YOUR_*` placeholders

### 4. Activate & Test
Detailed testing steps in [SETUP.md](./SETUP.md#step-6-activate--test)

---

## 🔌 Integrations

| Service | Used In | Purpose |
|:--------|:--------|:--------|
| QuickBooks Online | 01, 02, 03 | Core accounting engine |
| OpenAI (GPT-4o-mini) | 01, 02, 03 | AI extraction & profiling |
| Notion | 01, 02, 03, 04 | CRM, logging, reporting |
| Gmail | 01, 02, 03, 04 | Notifications & alerts |
| Google Calendar | 01 | Kickoff meeting scheduling |
| Google Drive | 03 | Receipt archival |
| Qdrant | 03 | Categorization learning *(optional)* |

---

## 🔧 Configuration

All placeholders use the `YOUR_` prefix for easy find-and-replace:

```
YOUR_OPENAI_CREDENTIAL_ID
YOUR_QB_OAUTH_CREDENTIAL_ID
YOUR_NOTION_CREDENTIAL_ID
YOUR_GMAIL_CREDENTIAL_ID
YOUR_GOOGLE_CALENDAR_CREDENTIAL_ID
YOUR_GOOGLE_DRIVE_CREDENTIAL_ID
YOUR_QDRANT_CREDENTIAL_ID
YOUR_NOTION_*_DB_ID
your-ops-email@company.com
```

---

## 📁 Repo Structure

```
QB_Autopilot_Suite/
├── 01_QB_Client_Onboarding_Orchestrator.json   # Client intake pipeline
├── 02_QB_Invoice_Processing_Hub.json           # AI invoice processing
├── 03_QB_Expense_Automation_Engine.json        # Smart expense handling
├── 04_QB_Master_Control_Dashboard.json         # Monitoring & reporting
├── README.md                                    # You are here
├── SETUP.md                                     # Installation guide
├── CREDENTIALS.md                               # API credential setup
├── LICENSE                                      # MIT License
└── .gitignore
```

---

## 📖 Documentation

| Doc | Purpose |
|:----|:--------|
| [SETUP.md](./SETUP.md) | Step-by-step installation, Notion DB schemas, testing |
| [CREDENTIALS.md](./CREDENTIALS.md) | OAuth setup for all 7 services with links & scopes |

---

## 🤝 Contributing

Found a bug? Have an improvement? PRs welcome.

1. Fork the repo
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📄 License

Distributed under the MIT License. See [LICENSE](./LICENSE) for details.

---

<div align="center">

**Built with 🤖 + ☕**

*They say the blind can't lead the blind. But I can lead the way.*

</div>
