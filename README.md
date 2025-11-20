

# **Teams Enterprise Knowledge Assistant**

A Node.js backend that powers a Microsoft Teams assistant capable of answering employee questions by querying **ServiceNow** and **SharePoint**, using **OpenAI** to generate a unified, summarised response.

This is a first-draft, functional prototype showcasing how GenAI can be applied to enterprise search and workflow automation.

---

## **Features**

* Natural-language query endpoint (`/api/query`)
* Calls OpenAI to understand intent and summarise results
* Searches:

  * **ServiceNow KB** (live or mocked)
  * **SharePoint Documents** (mocked in v1)
* Aggregates data from multiple systems
* Returns a single answer with referenced sources
* Teams Bot Framework endpoint stub (`/api/messages`) for future integration

---

## **Architecture (Summary)**

```
Teams (future) → Bot Framework → Node.js Backend → 
  ├─ ServiceNow REST API
  ├─ SharePoint / Microsoft Graph (mocked)
  └─ OpenAI Reasoning & Summarisation
```

The backend handles the orchestration between all systems and produces a clean, human-readable answer.

---

## **Project Structure**

```
src/
  app.js
  routes/
    queryRoute.js
    teamsRoute.js
  services/
    openaiClient.js
    servicenowClient.js
    sharepointClient.js
    aggregator.js
.env.example
package.json
README.md
```

---

## **Setup**

### 1. Install dependencies

```bash
npm install
```

### 2. Create a `.env` file

```
OPENAI_API_KEY=your_key_here

# Optional (can be mocked)
SN_INSTANCE_URL=https://devXXXXX.service-now.com
SN_USER=admin
SN_PASS=password
```

### 3. Run locally

```bash
npm run dev
```

Server runs on:

```
http://localhost:3000
```

---

## **How to Use**

### **Query endpoint**

```
POST /api/query
```

Example request:

```json
{
  "query": "How do I request a laptop?"
}
```

Example response:

```json
{
  "answer": "You can request a laptop through the Service Catalog...",
  "snResults": [...],
  "spResults": [...]
}
```

---

## **Notes**

* SharePoint search is mocked in the first draft.
* ServiceNow search can run either live (REST API) or in mock mode.
* `/api/messages` exists as a placeholder for Teams integration and will be expanded later.

---

## **Roadmap**

* Full Teams bot implementation
* Real Microsoft Graph search
* Adaptive Cards for richer responses
* Multi-turn chat context
* Optional vector database for RAG
* Additional system connectors (Jira, Confluence, Workday, etc.)

---

## **Purpose**

This repository demonstrates a practical GenAI-based enterprise solution with real integrations and clean architecture suitable for showcasing in technical applications or AI engineering portfolios.

---
