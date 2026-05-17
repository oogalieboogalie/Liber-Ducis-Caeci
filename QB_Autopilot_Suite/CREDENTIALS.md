# Credentials Guide — QB Autopilot Suite

Every external service requires credentials configured in n8n. This guide walks you through each one.

---

## 1. QuickBooks Online OAuth2

**Used in:** Workflows 01, 02, 03

### Setup Steps:
1. Go to [Intuit Developer Portal](https://developer.intuit.com/)
2. Create an app → Select **QuickBooks Online Accounting**
3. Set redirect URI to: `https://YOUR_N8N_DOMAIN/rest/oauth2-credential/callback`
4. Copy **Client ID** and **Client Secret**

### n8n Configuration:
- **Credential Type:** QuickBooks OAuth2 API
- **Client ID:** *(from Intuit developer portal)*
- **Client Secret:** *(from Intuit developer portal)*
- **Environment:** Production *(or Sandbox for testing)*
- **Scopes:** `com.intuit.quickbooks.accounting`

### Required API Scopes:
| Scope | Purpose |
|:------|:--------|
| `com.intuit.quickbooks.accounting` | Full read/write access to QB data |

### Notes:
- OAuth2 tokens expire — n8n handles refresh automatically
- Test with Sandbox environment first before switching to Production
- You need a QuickBooks Online subscription (Simple Start or higher)

---

## 2. OpenAI API

**Used in:** Workflows 01, 02, 03

### Setup Steps:
1. Go to [OpenAI Platform](https://platform.openai.com/)
2. Navigate to **API Keys** → **Create new secret key**
3. Copy the key (you won't see it again)

### n8n Configuration:
- **Credential Type:** OpenAI API
- **API Key:** *(your secret key)*

### Model Used:
- `gpt-4o-mini` — Used for invoice extraction, receipt analysis, and client profiling
- You can swap to `gpt-4o` for higher accuracy (higher cost)

### Estimated Usage:
- ~$0.01-0.05 per invoice/receipt processed
- ~$0.02-0.08 per client profile generated

---

## 3. Notion API

**Used in:** Workflows 01, 02, 03, 04

### Setup Steps:
1. Go to [Notion Integrations](https://www.notion.so/my-integrations)
2. Click **New integration**
3. Name it (e.g., "QB Autopilot")
4. Select your workspace
5. Copy the **Internal Integration Secret**
6. **IMPORTANT:** Share each Notion database with your integration:
   - Open database → ••• menu → **Connections** → Add your integration

### n8n Configuration:
- **Credential Type:** Notion API
- **API Key:** *(Internal Integration Secret)*

### Permissions Needed:
- Read content
- Insert content
- Update content

---

## 4. Gmail OAuth2

**Used in:** Workflows 01, 02, 03, 04

### Setup Steps:
1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a project (or use existing)
3. Enable **Gmail API**
4. Go to **Credentials** → **Create Credentials** → **OAuth 2.0 Client ID**
5. Application type: **Web application**
6. Add redirect URI: `https://YOUR_N8N_DOMAIN/rest/oauth2-credential/callback`
7. Copy **Client ID** and **Client Secret**

### n8n Configuration:
- **Credential Type:** Gmail OAuth2
- **Client ID:** *(from Google Cloud Console)*
- **Client Secret:** *(from Google Cloud Console)*
- Click **Connect** to authorize

### Required Scopes:
- `https://www.googleapis.com/auth/gmail.send`
- `https://www.googleapis.com/auth/gmail.compose`

---

## 5. Google Calendar OAuth2

**Used in:** Workflow 01

### Setup Steps:
1. In the same Google Cloud project, enable **Google Calendar API**
2. Use the same OAuth2 client or create a new one
3. Same redirect URI as Gmail

### n8n Configuration:
- **Credential Type:** Google Calendar OAuth2
- **Client ID:** *(same as Gmail or separate)*
- **Client Secret:** *(same as Gmail or separate)*

### Required Scopes:
- `https://www.googleapis.com/auth/calendar`
- `https://www.googleapis.com/auth/calendar.events`

---

## 6. Google Drive OAuth2

**Used in:** Workflow 03

### Setup Steps:
1. In the same Google Cloud project, enable **Google Drive API**
2. Use the same OAuth2 client or create a new one

### n8n Configuration:
- **Credential Type:** Google Drive OAuth2
- **Client ID:** *(same as Gmail or separate)*
- **Client Secret:** *(same as Gmail or separate)*

### Required Scopes:
- `https://www.googleapis.com/auth/drive.file`

### Setup Notes:
- Create a folder in Google Drive for receipt archival
- Update the folder ID in the "Archive Receipt to Drive" node in Workflow 03

---

## 7. Qdrant API *(Optional)*

**Used in:** Workflow 03

### Setup Steps:

**Option A — Local Docker:**
```bash
docker run -p 6333:6333 -p 6334:6334 qdrant/qdrant
```

**Option B — Qdrant Cloud:**
1. Go to [Qdrant Cloud](https://cloud.qdrant.io/)
2. Create a cluster
3. Copy the URL and API key

### n8n Configuration:
- **Credential Type:** Qdrant API
- **URL:** `http://localhost:6333` *(or your cloud URL)*
- **API Key:** *(if using Qdrant Cloud)*

### Collection Setup:
Create a collection named `expense_learning`:
```bash
curl -X PUT 'http://localhost:6333/collections/expense_learning' \
  -H 'Content-Type: application/json' \
  -d '{
    "vectors": {
      "size": 1536,
      "distance": "Cosine"
    }
  }'
```

---

## Credential Reference Table

| Placeholder in Workflows | Credential Type | Service |
|:--------------------------|:----------------|:--------|
| `YOUR_QB_OAUTH_CREDENTIAL_ID` | QuickBooks OAuth2 API | QuickBooks Online |
| `YOUR_OPENAI_CREDENTIAL_ID` | OpenAI API | OpenAI |
| `YOUR_NOTION_CREDENTIAL_ID` | Notion API | Notion |
| `YOUR_GMAIL_CREDENTIAL_ID` | Gmail OAuth2 | Gmail |
| `YOUR_GOOGLE_CALENDAR_CREDENTIAL_ID` | Google Calendar OAuth2 | Google Calendar |
| `YOUR_GOOGLE_DRIVE_CREDENTIAL_ID` | Google Drive OAuth2 | Google Drive |
| `YOUR_QDRANT_CREDENTIAL_ID` | Qdrant API | Qdrant |
