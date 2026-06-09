# AI Delivery Lead - Comprehensive AI Delivery Framework

*Source file: `AI Delivery Lead - Comprehensive AI Delivery Framework.xlsx`*  
*Sheets: Initiatives & Projects, Budget & Strategy, Technology Stack, Governance & Compliance, RAID Log, Agile Backlog*

---

## Purpose

This document captures the end-to-end plan for enterprise AI delivery. It combines strategic initiatives, budget assumptions, platform architecture, governance controls, risk tracking, and the initial delivery backlog.

## Executive summary

- Build a secure, UAE-resident AI platform by combining Azure-native services, private networking, and strong identity controls.
- Prioritize enterprise RAG and regulatory use cases while enforcing model risk, content safety, and auditability.
- Align platform investment to enable core AI orchestration, search-based retrieval, and governance at scale.

---

## Initiatives & Projects

This section defines the AI initiative portfolio and the expected business value for each program.

| Strategic Focus | Project ID | Use Case | Business Domain | AI Delivery Strategy | Target Value |
| --- | --- | --- | --- | --- | --- |
| Platform Foundation | P-00 | Central AI Orchestration Engine | Enterprise IT | API Router + Cosmos Logging + Content Filter | Enables all downstream AI. Prevents shadow IT. |
| Ops Efficiency | P-01 | Internal SOP & Policy Q&A | Retail Operations | RAG Pipeline querying ADCB SharePoint policies | Reduces policy search time by 80% for branch staff. |
| Compliance & Risk | P-02 | CBUAE Notice Summarizer | Legal & Compliance | Document classification + summarization prompt chain | Accelerates regulatory response times. |
| Customer Journey | P-03 | Loan Underwriting Copilot | Credit Risk | Secure RAG on customer financial statements (PII Masked) | Decreases loan decision SLA by 2 days. |
| Ops Efficiency | P-04 | IT Helpdesk Log Analyzer | IT Ops | Few-shot classification of server error logs | Reduces Mean Time to Resolution (MTTR). |


---

## Budget & Strategy

The estimated monthly Azure run rate supports a secure, compliant enterprise AI platform.

| Service Component | Sizing / Tier | Monthly Cost (USD) | Monthly Cost (AED) | Cost Type | Purpose |
| --- | --- | --- | --- | --- | --- |
| Azure OpenAI Service | PTU provisioned – GPT-4o | 7,000 | 25,690 | OPEX | Guaranteed throughput, predictable latency, and UAE data residency |
| Azure AI Search | Standard S2 | 1,200 | 4,404 | OPEX | Vector store for enterprise RAG and semantic search |
| Azure API Management | Premium Tier | 2,800 | 10,276 | OPEX | Secure API ingress, routing, throttling, and version control |
| Azure App Services / Functions | Premium P1v3 x4 | 1,000 | 3,670 | OPEX | Hosts orchestration layer, FastAPI services, and backend microservices |
| Azure Cosmos DB | Autoscale 1,000 RU/s | 500 | 1,835 | OPEX | Immutable audit logging for prompts, responses, and metadata |
| Storage & Networking | ZRS + Private Link | 500 | 1,835 | OPEX | Secure document storage and private connectivity |
| Application Insights / Log Analytics | 500 GB / month | 1,500 | 5,505 | OPEX | Observability, tracing, analytics, and alerting |
|  | TOTAL MONTHLY AZURE OPEX | 14,500 | 53,215 |  |  |

---

## Technology Stack

Each layer below supports secure, compliant AI delivery with clear separation of responsibility.

| Layer | Azure Service | Implementation Notes | Security / Compliance Mandate |
| --- | --- | --- | --- |
| Traffic Ingress | Azure Front Door / Application Gateway WAF | Inspects and filters inbound banking channel traffic | DDoS protection, OWASP rules, bot filtering, geo-fencing |
| API Routing | Azure API Management | Single entry point for AI requests; applies authentication, throttling, and policy enforcement | OAuth2 / Entra ID, PII header stripping, tiered rate limiting |
| Identity & Access | Microsoft Entra ID | Manages user and service identities with RBAC | Conditional access, least privilege, MFA, role-based prompt access |
| Compute & Orchestration | Azure App Service / AKS | Hosts AI router, RAG orchestration, tool calling, and model routing | Private VNet only, no public inbound IPs, managed identities |
| Workflow Execution | Azure Durable Functions / Logic Apps | Coordinates multi-step AI workflows, tool calls, and validation | Traceability, timeout policies, safe retry logic |
| Generative Models | Azure OpenAI Service | GPT-4o inference plus embeddings | Private endpoint, no training usage, UAE data residency compliance |
| Prompt Management | Azure Blob Storage + GitHub / Azure DevOps | Version control for prompts, templates, and evaluation artifacts | Change control, audit trail, gated deployment |
| Retrieval Storage | Azure AI Search | Stores document chunks, embeddings, and metadata filters | CMK encryption, RBAC retrieval controls, metadata tagging |
| Data Storage | Azure Data Lake Storage Gen2 / Blob Storage | Holds raw and processed enterprise documents for ingestion | Encryption at rest, classification tags, retention policies |
| Pre-LLM Tokenization | Azure Functions + Custom Tokenization | Masks sensitive data before storage or LLM submission | No raw PII enters vector DB or model context; audited detokenization |
| Audit & Telemetry | Azure Cosmos DB + App Insights + Log Analytics | Logs full interaction traces, latency, and user context | Immutable logs, 7-year retention, optional WORM support |
| Observability | Azure Monitor + Prometheus + Grafana | Tracks infrastructure, AI metrics, and FinOps usage | Anomaly detection for drift, latency, and cost |
| Secrets Management | Azure Key Vault (HSM-backed) | Stores secrets, keys, and certificates | Managed identity access only, automated rotation |
| Content Safety | Azure AI Content Safety | Filters unsafe prompts and responses before LLM execution | Prevents prompt injection, PII leakage, and jailbreaks |
| Data Governance | Microsoft Purview | Classifies data, tracks lineage, and labels sensitivity | GDPR, UAE PDPL, and internal banking policy compliance |
| Model Evaluation | Azure ML + Custom Pipelines | Runs hallucination tests, retrieval scoring, and prompt A/B experiments | Model risk controls and approval gates before production |
| FinOps Governance | Azure Cost Management + FinOps Dashboards | Monitors token spend and usage by business process | Budget enforcement, spend alerts, and cost-based routing |
| Network Security | Azure VNet + Private Link + NSG | Isolates AI resources inside a secure network | No public exposure, east-west inspection, zero-trust architecture |

---

## Governance & Compliance

This checklist assures adherence to CBUAE and enterprise AI governance expectations.

| Control ID | Domain | Requirement | Enforcement | Validation |
| --- | --- | --- | --- | --- |
| CTL-01 | Data Privacy | Do not send customer PII to external model providers | Use Azure OpenAI inside ADCB VNet and apply regex-based PII masking/tokenization | Penetration testing and packet inspection |
| CTL-02 | Auditability | Trace automated decisions to exact inputs for 7 years | Log prompt IDs, inputs, outputs, citations, and timestamps in Cosmos DB | Internal audit review and query validation |
| CTL-03 | Bias & Fairness | Prevent discrimination from AI outputs | Conduct drift analysis, red teaming, and exclude direct credit scoring initially | QA regression test suites |
| CTL-04 | Security | Mitigate LLM-specific risks, including prompt injection | Apply Azure AI Content Safety and strict gateway validation | Automated injection testing |

---

## RAID Log

Track the program’s risks, assumptions, issues, and dependencies.

| Type | ID | Description | Impact | Mitigation / Action | Owner | Status |
| --- | --- | --- | --- | --- | --- | --- |
| Risk | R-01 | CBUAE may impose stricter data residency rules mid-project | High | Keep architecture localized to Azure UAE North and avoid global-only services | Delivery Lead | Open |
| Risk | R-02 | AI hallucinations could damage the bank's reputation | High | Enforce RAG grounding, low temperature for regulated cases, and mandatory citations | Platform Team | Open |
| Assumption | A-01 | Azure UAE North has sufficient GPT-4o PTU quota for enterprise scale | High | Request quota early and maintain Microsoft engagement | DevOps Team | Closed |
| Issue | I-01 | Legacy core banking systems lack real-time AI APIs | Medium | Use daily batch extracts into Data Lake until APIs are modernized | Platform Team | Open |
| Dependency | D-01 | InfoSec approval needed for VNet private endpoint connectivity | High | Engage CISO architecture review board with threat model documentation | Delivery Lead | In Progress |

---

## Agile Backlog

Initial delivery tasks for platform engineering, RAG, and governance.

| Epic | User Story | Task ID | Task | Acceptance Criteria | Assignee | Status |
| --- | --- | --- | --- | --- | --- | --- |
| Core AI Orchestrator | US1.1: As a system, I need secure AI ingress | TSK-001 | Provision Azure APIM in VNet | APIM is deployed inside a VNet and public IP access is disabled | DevOps Eng | To Do |
| Core AI Orchestrator | US1.1: As a system, I need secure AI ingress | TSK-002 | Configure APIM JWT validation | APIM rejects requests without valid Entra ID token | Platform Eng | To Do |
| Core AI Orchestrator | US1.2: As a risk owner, I need audit logging | TSK-003 | Build FastAPI logging middleware | Middleware logs requests/responses to Cosmos DB asynchronously | Platform Eng | To Do |
| Enterprise RAG Engine | US2.1: As a bot, I need to search banking policies | TSK-004 | Implement PDF chunking for Azure AI Search | PDFs parsed; 1,000-token chunks; 150-token overlap; metadata retained | AI Eng | To Do |
| Enterprise RAG Engine | US2.1: As a bot, I need vector search | TSK-005 | Deploy Azure AI Search index | Vector field created and HNSW configured | Data Eng | To Do |
| AI Security & Guardrails | US3.1: As a CISO, I need to block prompt injections | TSK-006 | Integrate Azure AI Content Safety | Jailbreak attempts blocked and harmful content filtered | QA/Eval Eng | To Do |


---
