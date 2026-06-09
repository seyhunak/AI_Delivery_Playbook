# AI Delivery Lead - RM Assistant Project

*Source file: `AI Delivery Lead - RM Assistant Project.xlsx`*  
*Sheets: Requirements · Architecture & Security · RAG & Model Selection · Data Sources · Rollout Plan · Success Metrics*

---

## Purpose

This document defines the Reference Model Assistant project for private banking relationship managers. It captures functional requirements, architecture standards, retrieval architecture, data sources, rollout milestones, and success metrics for a compliant, grounded RM productivity platform.

---

## How to use this document

- Use the Requirements section to validate the use case and acceptance criteria.
- Use Architecture & Security to confirm the platform design and controls.
- Use RAG & Model Selection to enforce retrieval and model performance expectations.
- Use the Rollout Plan and Success Metrics to drive delivery and measure value.

---

## Requirements

| Category | Requirement | Description | Acceptance Criteria |
| --- | --- | --- | --- |
| Contextual summaries | Functional | Real-time synthesis of relationship histories, contact reports, and financial positions | Generated in < 3s; accurately reflects last 5 CRM touchpoints |
| Advisory matching | Functional | Align client profiles to investment mandates and product rules | Correctly cross-references risk profile with product prospectus |
| Drafting automation | Functional | Auto-generate client emails and contact reports | Matches approved tone; zero hallucination of financial figures |
| Semantic search | Functional | Natural language search across research docs and market data | Returns grounded snippets with direct citation links |
| Performance | Non-functional | Fast chat and retrieval response times | P95 latency < 2.5s with 50 active concurrent users |
| Availability | Non-functional | High availability across Azure regions | Failover completes in < 5 minutes |
| Accuracy | Non-functional | No ungrounded financial outputs | Groundedness score > 4.8 / 5.0 on continuous evaluation |

---

## Architecture & Security

| Layer | Component | Service | Purpose | Security Standard |
| --- | --- | --- | --- | --- |
| Front-end | CRM Integration | Dynamics / Web App | Embedded assistant UI in RM workspace | Entra ID SSO; conditional access |
| API Gateway | Traffic control | Azure API Management | Routing, throttling, auditing | Private endpoint, VNet-only access |
| Orchestration | Conversation engine | Azure App Service + Semantic Kernel | Manages state, memory, tool calls | System-assigned managed identity, no secrets in code |
| Model provider | LLMs & embeddings | Azure OpenAI Service | GPT-4o reasoning, text-embedding-3 vectors | Azure AI Content Safety, data logging disabled |
| Knowledge base | Vector store | Azure AI Search | Hybrid vector / semantic search indexes | RBAC to index layer, CMK encryption at rest |
| Data ingestion | Document pipeline | Azure AI Document Intelligence + ADF | PDF parsing and CRM data sync | PII redaction and masking before indexing |
| Network | Isolation | Azure Virtual Network | Hub-and-spoke service isolation | No public internet access, strict NSGs |

---

## RAG & Model Selection

| Stage | Service | Configuration | Purpose | SLA / Target |
| --- | --- | --- | --- | --- |
| Data extraction | Azure AI Document Intelligence | Layout model (prebuilt) | Extract tables, paragraphs, and structure from documents | Batch / async processing |
| Embedding generation | text-embedding-3-large | 1536 dims | Encode text chunks for semantic similarity | < 200ms per request |
| Retrieval | Azure AI Search | Hybrid search + semantic ranker | Retrieve top-K chunks by keyword, vector, and semantics | < 500ms response |
| Intent routing | GPT-4o-mini | Pay-as-you-go | Classify intent and route simple queries | < 800ms response |
| Complex reasoning | GPT-4o | Provisioned throughput | Synthesize multi-doc research and portfolio guidance | < 1.5s response |

---

## Data Sources

| Domain | System | Data Type | Frequency | PII / Sensitivity Controls |
| --- | --- | --- | --- | --- |
| Client profiles | Dynamics CRM / Core Banking | Structured (KYC, risk profile, net worth) | Near real-time | Mask account numbers and personal contact details |
| Portfolio data | Wealth management system | Structured (positions, allocations) | Daily batch | Retain percentages; mask absolute values where feasible |
| Research content | SharePoint / internal drives | Unstructured (market briefs, product papers) | Hourly sync | Public / internal market data; low sensitivity |
| Interaction logs | Email archives / CRM notes | Unstructured (past meetings, notes) | Real-time | NER-based redaction before embedding |

---

## Rollout Plan

| Phase | Timeline | Focus | Key Activities | Exit Criteria |
| --- | --- | --- | --- | --- |
| Alpha | Months 1-2 | Core platform and control foundation | Build VNet, deploy Azure OpenAI, establish RAG pipeline with synthetic data | Landing zone security sign-off; stable test responses |
| Alpha | Months 1-2 | Power user pilot | Deploy to 5 RMs for internal research queries | Feedback loop established; baseline latency targets met |
| Beta | Months 3-4 | CRM and live-data integration | Connect read-only CRM data and ingest contact reports | Purview audit shows zero PII leakage |
| Beta | Months 3-4 | Expanded RM pilot | Grow pilot to 50 RMs, refine prompts for real portfolios | Groundedness > 4.8 consistently |
| Scale | Months 5-6 | Division rollout | Deploy across Private Banking; enable email/contact drafting | Load test supports 500+ concurrent users |
| Scale | Months 5-6 | Optimization | Publish ROI dashboards and evaluate fine-tuning | MAU adoption > 80% within 90 days |

---

## Success Metrics

| Pillar | Metric | Target | Tool | Review cadence |
| --- | --- | --- | --- | --- |
| Infrastructure | Availability | >= 99.95% | Azure Monitor | Continuous |
| Infrastructure | P95 latency | < 2.5s | Application Insights | Daily |
| AI operations | Groundedness score | > 4.8 / 5.0 | Azure AI Studio | Weekly |
| AI operations | Retrieval quality (NDCG@10) | > 0.85 | Azure AI Search logs | Weekly |
| AI operations | Token efficiency | < 5% waste | Azure API Management logs | Monthly |
| Business value | Prep time reduction | 40% reduction in meeting prep | User surveys / telemetry | Monthly |
| Business value | Platform adoption | > 80% MAU in 90 days | Power BI / App Insights | Weekly |

---

## Notes

- This project is scoped for a regulated private banking environment with a strong focus on grounding, privacy, and auditability.
- Validate every new data source with Privacy, Legal, and Security before inclusion.
- Use the success metrics to gate the broader rollout from Beta to Scale.

