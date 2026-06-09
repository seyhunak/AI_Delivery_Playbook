# AI Delivery Lead - Delivery Technology Choice Matrix

*Source file: `AI Delivery Lead - Delivery Technology Choice Matrix.xlsx`*  
*Sheet: Technology Matrix*

---

## Overview

This matrix maps enterprise AI delivery capabilities to Azure services, highlighting when each service is the recommended choice and why it is preferred. Use it as a reference for architecture decisions, service selection, and cross-team alignment.

---

## How to use this matrix

1. Find the capability you need.
2. Review the recommended Azure service.
3. Confirm the choice with enterprise architecture, security, and FinOps requirements.

---

## Technology Matrix

| Capability | Azure Service | When to Use | Why Chosen |
| --- | --- | --- | --- |
| Identity and access | Azure Entra ID | Every AI solution | Enterprise SSO, RBAC, and conditional access |
| Secrets management | Azure Key Vault | API keys, certificates, credentials | Secure secret storage with managed identity support |
| API gateway | Azure API Management | Expose AI services to channels | Governance, throttling, authentication and policies |
| Generative AI models | Azure OpenAI Service | Managed GPT workloads | Enterprise-grade GPT deployment, controls, and compliance |
| AI development platform | Azure AI Foundry | AI project lifecycle | Centralized AI lifecycle and collaboration capabilities |
| Enterprise search | Azure AI Search | RAG implementations | Native vector + keyword search, semantic search enabled |
| Document intelligence | Azure AI Document Intelligence | PDFs, forms, contracts | OCR plus structured extraction for documents |
| Speech services | Azure AI Speech | Voice assistants | Speech-to-text and text-to-speech with voice customization |
| Translation services | Azure AI Translator | Multi-language support | Managed enterprise translation with broad language support |
| Vision and image analysis | Azure AI Vision | Image/document analysis | Managed computer vision with OCR and visual AI |
| Workflow automation | Azure Logic Apps | Low-code business workflows | Orchestration for integration and approvals |
| Serverless compute | Azure Functions | Event-driven automation | Lightweight serverless execution for microservices |
| Stateful orchestration | Durable Functions | Multi-step AI workflows | Reliable orchestration for long-running processes |
| Enterprise messaging | Azure Service Bus | Reliable integration | Guaranteed delivery with enterprise messaging patterns |
| Event streaming | Azure Event Hub | High-volume streaming | Scalable event ingestion for telemetry and analytics |
| Event routing | Azure Event Grid | Reactive architectures | Event distribution and serverless triggers |
| Managed APIs | Azure App Service | Business APIs | Simplified managed hosting for HTTP APIs |
| Container orchestration | Azure Kubernetes Service (AKS) | Enterprise-scale container workloads | Scalable container orchestration with policy control |
| Container registry | Azure Container Registry | Container storage | Secure registry for container images |
| Infrastructure provisioning | Terraform + Azure | Environment provisioning | Repeatable infrastructure deployments across environments |
| CI/CD pipelines | Azure DevOps Enterprise | Delivery pipelines and approvals | Enterprise pipeline automation with approvals and governance |
| Source control | Azure Repos | Code management | Enterprise Git hosting integrated with Azure DevOps |
| Agile delivery | Azure Boards | Planning and tracking | Backlog management, sprint planning, and reporting |
| Documentation | Azure DevOps Wiki | Delivery documentation | Integrated documentation with versioning |
| Infrastructure monitoring | Azure Monitor | Resource observability | Central platform for infrastructure metrics and alerting |
| Log analytics | Log Analytics Workspace | Operational telemetry analysis | Central log storage and query capabilities |
| Application monitoring | Application Insights | API and app monitoring | Performance and usage visibility for applications |
| Security monitoring | Microsoft Sentinel | SOC integration | SIEM for threat detection and incident response |
| Data foundation | Azure Data Lake Storage Gen2 | AI data foundation | Scalable, secure storage for structured and unstructured data |
| Data integration | Azure Data Factory | ETL and data movement | Enterprise data integration and transformation |
| Analytics | Azure Databricks | Data engineering and ML | Large-scale processing and collaborative analytics |
| ML lifecycle | Azure Machine Learning | Model training and deployment | End-to-end ML lifecycle management |
| Feature store | Azure ML Feature Store | Feature reuse and governance | Consistent feature definitions and discoverability |
| Data governance | Microsoft Purview | Data catalog and lineage | Regulatory compliance, cataloging, and lineage |
| Cost governance | Azure Cost Management | Spend visibility | Budgeting, monitoring, and cost optimization |
| Backup | Azure Backup | Business continuity | Managed backup for VMs, databases, and storage |
| Disaster recovery | Azure Site Recovery | Resilience and failover | DR planning with automated failover |

---

## Notes

- This matrix assumes an Azure-first enterprise architecture.
- Validate service choices with security, networking, and FinOps before implementation.
- Favor managed Azure services to reduce custom infrastructure and simplify governance.

