# AI & Operations Automation Portfolio
**By Mark Khalaf | Technical Computer Science Engineer**

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

## Tech Stack & Skills
- **Automation:** n8n, Make.com, Webhooks, Recursive Looping, Batch Processing.
- **AI:** Google Gemini, Prompt Engineering, OCR, LLM-Data Extraction.
- **Backend:** JavaScript (Node.js logic), REST API Integration, JSON Transformation.
- **Infrastructure:** Self-hosted n8n, API Security, OAuth2, Error Handling.
- **Tools:** Airtable, Google Sheets, Slack API, Postman, Git/GitHub.
