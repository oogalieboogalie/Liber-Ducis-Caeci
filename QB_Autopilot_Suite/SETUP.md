# Setup Guide — QB Autopilot Suite

## Prerequisites

- **n8n** v1.0+ (self-hosted or cloud)
- **QuickBooks Online** account with API access
- **OpenAI** API key (GPT-4o-mini access)
- **Notion** integration + workspace
- **Gmail** account with OAuth2
- **Google Calendar** API access
- **Google Drive** API access
- **Qdrant** instance (local Docker or cloud) — *optional, for Expense Engine learning*

---

## Step 1: Import Workflows

Import in this order (some workflows reference others):

1. `01_QB_Client_Onboarding_Orchestrator.json`
2. `02_QB_Invoice_Processing_Hub.json`
3. `03_QB_Expense_Automation_Engine.json`
4. `04_QB_Master_Control_Dashboard.json`

**How to import:**
1. Open your n8n instance
2. Click **"Add workflow"** → **"Import from File"**
3. Select the JSON file
4. **Do NOT activate yet** — configure credentials first

---

## Step 2: Configure Credentials

See [CREDENTIALS.md](./CREDENTIALS.md) for detailed credential setup instructions.

After creating each credential in n8n, update the credential references in each workflow:

1. Open each workflow
2. Click on nodes that show credential errors (they'll have a red warning)
3. Select your newly created credentials from the dropdown
4. Save

---

## Step 3: Create Notion Databases

You need **5 Notion databases**. Create them in a dedicated Notion workspace page.

### 3a. Client Master Database
**Used by:** Workflow 01 (Onboarding)

| Property | Type |
|:---------|:-----|
| Client ID | Title |
| Company Name | Text |
| Contact Email | Email |
| Industry | Text |
| Business Size | Text |
| Services Requested | Text |
| Monthly Revenue | Text |
| Complexity Score | Number |
| Implementation Timeline | Text |
| Priority Workflows | Text |
| Status | Select (Onboarding, Active, Paused) |
| QB Customer Created | Text |

### 3b. Invoice Processing Log
**Used by:** Workflow 02 (Invoice Hub)

| Property | Type |
|:---------|:-----|
| Invoice Number | Title |
| Vendor | Text |
| Amount | Number |
| Status | Select (Posted to QB, QB Error, Needs Review) |
| Confidence Score | Number |
| Processing ID | Text |

### 3c. Expense Tracking Log
**Used by:** Workflow 03 (Expense Engine)

| Property | Type |
|:---------|:-----|
| Merchant | Title |
| Amount | Number |
| Date | Text |
| Category | Text |
| Status | Select (Auto-Posted, Pending Approval) |
| Employee | Text |
| Client | Text |
| Processing ID | Text |
| Confidence | Number |

### 3d. System Health Log
**Used by:** Workflow 04 (Dashboard)

| Property | Type |
|:---------|:-----|
| Timestamp | Title |
| Overall Health | Select (healthy, degraded, critical) |
| Total Alerts | Number |
| Services Online | Number |
| Total Services | Number |
| Invoices Today | Number |
| Expenses Today | Number |
| New Clients Today | Number |
| API Calls Today | Number |
| Error Rate | Text |
| Alert Details | Text |

### 3e. Daily Reports Archive
**Used by:** Workflow 04 (Dashboard)

| Property | Type |
|:---------|:-----|
| Report Date | Title |
| Total Invoices | Number |
| Invoice Amount | Text |
| Total Expenses | Number |
| Expense Amount | Text |
| New Clients | Number |
| Success Rate | Text |
| System Uptime | Text |
| API Calls | Number |
| Top Insights | Text |

### After Creating Databases

1. Copy each database ID from the Notion URL
   - URL format: `notion.so/workspace/DATABASE_ID?v=...`
2. Replace the placeholder IDs in each workflow:
   - `YOUR_NOTION_CLIENT_MASTER_DB_ID`
   - `YOUR_NOTION_INVOICE_LOG_DB_ID`
   - `YOUR_NOTION_EXPENSE_LOG_DB_ID`
   - `YOUR_NOTION_HEALTH_LOG_DB_ID`
   - `YOUR_NOTION_DAILY_REPORTS_DB_ID`

---

## Step 4: Update Email Addresses

Search and replace `your-ops-email@company.com` with your actual operations email in all 4 workflows.

---

## Step 5: Set Up Qdrant (Optional)

The Expense Engine uses Qdrant for smart categorization learning. If you skip this, the workflow still works — it just won't learn from past categorizations.

**Quick Docker setup:**
```bash
docker run -p 6333:6333 -p 6334:6334 qdrant/qdrant
```

Create a collection named `expense_learning` in Qdrant.

---

## Step 6: Activate & Test

### Test Order:
1. **Onboarding** — Send a POST to `/webhook/client-onboard` with sample data:
   ```json
   {
     "company_name": "Test Company LLC",
     "contact_email": "test@example.com",
     "contact_phone": "555-0100",
     "industry": "consulting",
     "services_requested": "bookkeeping, quickbooks",
     "monthly_revenue": "15000"
   }
   ```

2. **Invoice Hub** — Send a POST to `/webhook/invoice-capture` with a PDF/image attachment

3. **Expense Engine** — Send a POST to `/webhook/expense-capture` with a receipt image

4. **Dashboard** — Activate and wait for the 15-minute health check cycle

---

## Troubleshooting

| Issue | Fix |
|:------|:----|
| Credential errors on nodes | Re-select credentials in each node's settings |
| QB API 401 errors | Refresh OAuth2 token in n8n credentials |
| Notion "database not found" | Verify database ID and that your integration has access |
| AI extraction returns bad JSON | Check OpenAI API key and model access |
| Qdrant connection refused | Ensure Qdrant is running on port 6333 |

---

## Next Steps

- **Customize email templates** in nodes to match your brand
- **Adjust auto-approval thresholds** in the Expense Engine's Business Rules Engine code node
- **Add Slack/Discord notifications** alongside Gmail alerts
- **Connect the Dashboard** to your actual n8n API for real health data (currently uses simulated data)
