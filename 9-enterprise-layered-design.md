# AI Delivery Lead - Enterprise Layered Design

*Source file: `AI Delivery Lead - Enterprise Layered Design.xlsx`*  
*Sheets: API Layer, Orchestration Layer, Knowledge Layer, Model Layer, Security Layer, Observability Layer*

---

## Purpose

This document defines the enterprise AI platform architecture as a layered design. It aligns core capabilities across API, orchestration, knowledge, model, security, and observability layers so governance, compliance, and delivery actions are visible to stakeholders.

## Design principles

- Secure by default: enforce zero-trust access, private networking, and policy-driven data control.
- Modular orchestration: separate API ingress, workflow logic, and model routing for resilience and cost control.
- Hybrid intelligence: combine vector retrieval, semantic search, and model inference with strong grounding.
- Compliance-first deployment: maintain UAE data residency, FAPI requirements, and immutable audit trails.
- Observability and FinOps: measure health, cost, and business impact with unified telemetry.

---

## API Layer

This layer provides secure, compliant access to AI services for external and internal channels while protecting backend models and data sources.

| Component | Capability | Use Case | Implementation | Compliance & Prerequisites | Delivery Actions | Status | Checklist |
| --- | --- | --- | --- | --- | --- | --- | --- |
| API Gateway (APIM) | Routing & ingress | Expose AI services securely to mobile banking, contact center, Copilot and partner channels | Azure API Management with OAuth2, JWT validation, SSL/TLS termination, WAF | UAE data residency, FAPI compliance, customer-facing API policies | 1. Provision APIM in UAE North. 2. Apply JWT validation policies. 3. Configure WAF and custom domains. | In Progress | Configure custom domains, SSL certs, and policy revisions |
| Authentication & Authorization | Identity control | Enforce zero-trust access across all consumers and services | Entra ID integration, app registrations, OAuth scopes, service principals | Entra ID P2, corporate security baseline, MFA | 1. Define app scopes and permissions. 2. Configure service principals and managed identities. | In Progress | Map AD groups to application roles and review access logs |
| Rate Limiting / Throttling | Cost protection | Protect downstream LLMs from abuse and control consumption costs | APIM policies implementing token-bucket limits by consumer tier | Cost center allocation, usage governance | 1. Define Bronze/Silver/Gold tiers. 2. Apply throttling/quotas in APIM. | In Progress | Set tier thresholds, monitor policy hits, adjust quotas |

---

## Orchestration Layer

Orchestration manages multi-step reasoning, workflow execution, prompt context, and model routing so AI requests are reliable, auditable, and cost-aware.

| Component | Capability | Use Case | Implementation | Compliance & Prerequisites | Delivery Actions | Status | Checklist |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Agent Framework | Multi-step reasoning | Execute complex banking workflows with state and memory | Foundry-based orchestration running containerized agents | Containerization standards, secure runtime controls | 1. Build Docker images. 2. Deploy to App Services or Kubernetes. | In Progress | Implement memory state management and service isolation |
| Prompt Management | Context injection | Version-control prompts and inject runtime context | Centralized prompt repository, GitOps pipeline, prompt templates | GitOps/CI-CD, review workflow | 1. Setup prompt repository. 2. Define templates and metadata. 3. Build release pipeline. | In Progress | Enable prompt versioning and pipeline validation |
| Workflow Engine | Automation | Coordinate async tasks and legacy core banking lookups | Azure Durable Functions or Logic Apps for long-running stateful workflows | Core banking API access, retry/circuit-breaker design | 1. Define durable workflows. 2. Build connectors to core systems. | In Progress | Define retry policies, backoff, and error handling |
| Model Routing | Cost & performance | Route requests to the best model based on cost, latency, capability | Python middleware with latency SLA and fallback logic | Latency SLA definitions, model risk governance | 1. Implement routing middleware. 2. Define fallback behavior. | In Progress | Configure fallback metrics, cost thresholds, and telemetry |

---

## Knowledge Layer

This layer captures, indexes, and serves business content so AI outputs remain grounded in verified enterprise data.

| Component | Capability | Use Case | Implementation | Compliance & Prerequisites | Delivery Actions | Status | Checklist |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Azure AI Search | Retrieval | Hybrid keyword + vector search for corporate documents | Azure AI Search index with semantic ranking and relevance tuning | Data classification, content hygiene, access policies | 1. Provision AI Search. 2. Build indexing pipeline. | In Progress | Configure chunking strategy, overlap and ranking criteria |
| Vector DB | Embedding store | Persist vectors for similarity search and RAG retrieval | Azure Cosmos DB with vector search and high-availability design | High availability, backup and restore | 1. Provision Cosmos DB. 2. Define embedding schema and dimensions. | In Progress | Establish model deployment connection and failover plan |
| Document Repositories | Ingestion | Ingest unstructured PDF/Word content and operational manuals | Azure Blob Storage with private endpoints and secure ingestion path | Malware scanning, content governance | 1. Deploy storage account. 2. Enable Defender for Storage. | In Progress | Configure lifecycle management, encryption, and scanning |
| SharePoint Integration | Sync | Sync HR policies and compliance guidelines continuously | Microsoft Graph delta sync connectors with scheduled updates | Service account provisioning, least-privilege access | 1. Create app registration. 2. Grant Graph read scopes. | In Progress | Establish App-only auth, secure permissions, and sync audit logs |

---

## Model Layer

The model layer supports current Azure OpenAI capabilities, alternative providers, and future model portability through abstraction.

| Component | Capability | Use Case | Implementation | Compliance & Prerequisites | Delivery Actions | Status | Checklist |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Azure OpenAI | LLM inference | Primary text summarization, logic, and banking response generation | GPT-4o / GPT-4o-mini in UAE Azure tenant with private endpoints | Quota approvals, regional deployment, data residency | 1. Request OpenAI quota. 2. Deploy model endpoints. 3. Configure private links. | In Progress | Request quota and validate network access |
| Claude (Anthropic) | Secondary model | Alternative provider for advanced reasoning, multilingual support, and specialized logic | Anthropic Claude via Bedrock or Azure-hosted endpoint | Cross-border data rules, model risk compliance | 1. Provision Claude endpoint. 2. Tune system prompts for banking. | In Progress | Validate compliance with cross-border rules and risk controls |
| Future Models | Model portability | Hot-swap to open-source or new proprietary models without rewiring | Abstract API wrapper using OpenAI-style schema | Model-agnostic design standards, schema versioning | 1. Build unified schema adapter. 2. Test payload transformations. | In Progress | Validate response mapping and fallback behavior |

---

## Security Layer

Security governs identities, secrets, network boundaries, and data access controls across all platform layers.

| Component | Capability | Use Case | Implementation | Compliance & Prerequisites | Delivery Actions | Status | Checklist |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Entra ID | Access governance | Centralize identity and enforce access policies | Conditional Access, MFA, service principals | MFA for developers, trusted IP restrictions | 1. Configure conditional access policies. 2. Review audit logs. | In Progress | Restrict access from trusted IP ranges |
| Key Vault | Secret management | Store keys, connection strings, certificates securely | Azure Key Vault with managed identities | Secret rotation policy, RBAC | 1. Provision Key Vault. 2. Assign managed identities. | In Progress | Automate rotation and access reviews |
| RBAC | Access boundaries | Enforce persona-based model and data access controls | Entra ID role mapping and fine-grained app permissions | Least privilege principle | 1. Create custom roles. 2. Map groups to roles. | In Progress | Define admin, developer, and consumer roles |
| Private Endpoints | Network isolation | Keep platform resources off the public internet | VNet injection and private endpoints for all PaaS resources | VNet architecture approval | 1. Create VNet and subnets. 2. Deploy private endpoints. | In Progress | Disable public access for all PaaS services |

---

## Observability Layer

Observability ensures the platform is measurable, auditable, and financially controlled.

| Component | Capability | Use Case | Implementation | Compliance & Prerequisites | Delivery Actions | Status | Checklist |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Azure Monitor | Infrastructure metrics | Monitor cluster and resource health centrally | Log Analytics workspace and diagnostic settings | Seven-year retention for financial logs | 1. Provision Log Analytics. 2. Enable diagnostics across resources. | In Progress | Configure critical CPU/memory alerts |
| Application Insights | Distributed tracing | Trace LLM execution, API flows, and exceptions | App Insights SDK in orchestration code | Data masking and telemetry sampling | 1. Inject SDK. 2. Configure telemetry sampling. | In Progress | Enable end-to-end transaction tracing |
| Cost Dashboard | FinOps visibility | Track token consumption and hosting costs | Custom Azure workbook with APIM and model telemetry | FinOps tagging strategy, budget policies | 1. Enforce resource tags. 2. Build cost workbook. 3. Setup alerts. | In Progress | Implement daily budget caps and spend alerts |
| Audit Logs | Regulatory audit | Preserve immutable interaction history for compliance | Immutable Log Analytics storage with retention locks | WORM storage, PII masking | 1. Enable immutable storage. 2. Configure retention locks. | In Progress | Ensure PII is masked before logging |

---

## Summary

This layered design provides a clear separation of concerns while supporting a secure, compliant enterprise AI platform. The current delivery focus is on establishing the API ingress, orchestration pipelines, knowledge retrieval systems, model provider flexibility, and the security/observability foundation needed for scalable deployment.
