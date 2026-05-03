# AI & Operations Automation Portfolio
**By Mark William | Technical Computer Science Engineer**

A collection of enterprise-grade automation systems designed for high-volume operations, focusing on scalability, data integrity, and deterministic AI logic.

---

## 1. Autonomous KYC & Visa Validation Pipeline
### [View System Architecture](workflow.png) | [View Workflow JSON File](KYC_Automation_Pipeline.json)

### Overview
A high-integrity, automated Know Your Customer (KYC) validation system designed to handle unstructured identity documents with a deterministic safety layer to eliminate human error and AI hallucinations.

### The Business Problem
Manual verification of identity documents (Visas/Passports) against applicant data is a high-latency bottleneck prone to human error and potential fraud, impacting placement speed in high-volume operational environments.

### System Architecture
- **Ingestion:** REST API / Webhooks via Postman.
- **Intelligence:** Google Gemini 1.5 Flash Vision (OCR extraction of unstructured ID data).
- **Validation Engine:** Custom JavaScript implementation of the Levenshtein Distance algorithm to normalize and validate name matches with a 95% threshold.
- **Data Persistence:** Airtable (CRM/ERP simulation).
- **Operational Logic:** Conditional routing for "Human-in-the-loop" overrides via Slack API on data discrepancies.

### Key Technical Features
- **Deterministic Reliability:** Uses hard-coded logic as a fail-safe for AI extraction to prevent false approvals.
- **API Resilience:** Implements secure header authentication and cross-platform data mapping.
- **High Agency Design:** Automatically flags high-risk mismatches for manual review, ensuring 100% data integrity before database entry.

---

## 2. Enterprise Data Migration Engine (Fault-Tolerant)
### [View System Architecture](migration_workflow.png) | [View Workflow JSON File](Enterprise_Data_Migration_Engine.json)

### Overview
A high-volume data migration and synchronization system engineered to process 500+ records while maintaining system stability and respecting third-party API rate limits.

### The Business Problem
Standard automations often crash during large-scale migrations due to memory overflows or "429 Too Many Requests" errors from destination APIs. This leads to data loss and manual reconciliation overhead.

### System Architecture
- **Scaling Logic:** Recursive loop architecture using **Split-in-Batches** nodes (50-record increments) to manage server load.
- **Rate Limiting:** Integrated a 5-second throttling delay (Wait Node) to ensure compliance with external API rate limits.
- **Fault Tolerance:** Configured an asynchronous error-handling branch that captures Axios/HTTP errors and logs them to Google Sheets/Airtable without halting the main migration process.
- **State Optimization:** Implemented "Execute Once" logic on notification triggers to prevent API spam and communication blockage.

### Key Technical Features
- **Batch Processing:** Successfully manages high-volume payloads by breaking them into manageable segments.
- **Resilient Error Logging:** Ensures 0% data loss by documenting every failed request for later reconciliation.
- **Operational Monitoring:** Provides a single, consolidated "Migration Complete" summary via Slack once the entire loop is successfully exited.

---

## 3. Autonomous B2B Lead Scoring Engine (RevOps)
### [View System Architecture](scoring_workflow.png) | [View Workflow JSON File](B2B_Lead_Scoring_Engine.json)

### Overview
A Revenue Operations (RevOps) automation that qualifies inbound leads in real-time using AI-driven scoring and firmographic extraction.

### The Business Problem
Sales teams often waste 30-40% of their time on low-quality leads. Manual qualification causes delays in responding to high-value "Hot" leads, leading to lost conversion opportunities.

### System Architecture
- **Ingestion:** Webhook-based trigger capturing raw lead data (Email, Name).
- **Enrichment Logic:** Custom JavaScript node to extract domains and prepare data for firmographic analysis.
- **AI Scoring Brain:** Gemini 1.5 Flash evaluates the lead against a defined Ideal Customer Profile (ICP), returning a structured score (1-10) and a qualitative reason.
- **Logic Routing:** A Switch node performs multi-path routing based on the AI-generated score.
- **Actions:** High-value leads trigger immediate Slack alerts for the sales team; low-value leads are automatically routed to a nurture campaign.

### Key Technical Features
- **Data Normalization:** Automated domain extraction from email strings to simplify lookup.
- **Contextual Intelligence:** Uses LLM reasoning to categorize company industry and potential value without manual research.
- **Speed-to-Lead:** Reduces lead qualification time from hours to milliseconds.

---

## 4. Asynchronous RAG Support Engine
### [View Main Workflow](main_arch.png) | [View Sub-Workflow](sub_arch.png)

### Overview
A decoupled support architecture designed to handle high-latency AI tasks (RAG) without triggering webhook timeouts in parent systems (Shopify/Zendesk).

### The Business Problem
Standard webhooks expect a response in <3 seconds. AI generation and Vector DB lookups often take 10+ seconds, leading to connection drops and failed integrations.

### System Architecture
- **Main Workflow:** Acts as a high-speed "Receiver" that responds with a `200 OK` instantly while passing the payload to a background process.
- **Sub-Workflow:** Operates asynchronously, performing a simulated RAG lookup and synthesizing a response using Gemini 1.5 Flash.
- **Fault Tolerance:** Robust JavaScript parsing ensures that even if the incoming JSON structure varies, the core query is extracted and processed.

### Tech Stack
- n8n (Asynchronous Orchestration)
- Google Gemini (LLM)
- JavaScript (Data Parsing)
- Slack API

---

## Tech Stack & Skills
- **Automation:** n8n, Make.com, Webhooks, Recursive Looping, Batch Processing.
- **AI:** Google Gemini, Prompt Engineering, OCR, LLM-Data Extraction.
- **Backend:** JavaScript (Node.js logic), REST API Integration, JSON Transformation.
- **Infrastructure:** Self-hosted n8n, API Security, OAuth2, Error Handling.
- **Tools:** Airtable, Google Sheets, Slack API, Postman, Git/GitHub.
