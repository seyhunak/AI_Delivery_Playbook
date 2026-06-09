# AI Delivery Lead - Platform KPI Targets

*Source file: `AI Delivery Lead - Platform KPI Target.xlsx`*  
*Sheet: Platform KPI*

---

## Overview

This KPI dashboard tracks the health and adoption of premium AI initiatives across infrastructure, application, AI, and business performance categories. It highlights priority amber items, the telemetry source for each metric, and recommended remediation actions.

---

## How to use this document

- Review each initiative’s amber metrics to identify current risk areas.
- Use the `Track` column to locate the metric in Azure observability tooling.
- Follow the `Action` column to close the gap with the most relevant operational response.

---

## Enterprise RAG Knowledge Base

| Category | Metric | Target | Current | Status | Track | Action |
| --- | --- | --- | --- | --- | --- | --- |
| Infrastructure | CPU utilization (%) | > 95 | 90.0 | Amber | Azure Monitor (AKS metrics) | Tune autoscaling and scale pods to absorb load |
| Infrastructure | Memory usage (%) | > 95 | 89.1 | Amber | Azure Monitor | Scale pod memory or optimize container memory usage |
| Infrastructure | Network throughput (MB/s) | > 8 | 8.0 | Green | Azure Network Watcher | Continue monitoring traffic and remove bottlenecks |
| Infrastructure | Availability (%) | > 95 | 99.0 | Green | Application Insights SLA | Maintain incident response readiness |
| Application | API latency (ms) | < 800 | 859 | Amber | Application Insights | Optimize prompt size, retrieval latency, and model routing |
| Application | Error rate (%) | < 2 | 2.0 | Green | Azure Monitor logs | Trigger alerts and investigate failure patterns |
| Application | Throughput (req/sec) | > 8 | 9.5 | Green | Application Insights | Review autoscaling and load balancing |
| Application | Cold start time (s) | < 8 | 8.2 | Amber | App telemetry / AKS startup logs | Keep warm pools for critical services |
| AI | Hallucination rate (%) | < 2 | 3.4 | Amber | Feedback loops & evaluation datasets | Improve RAG tuning and prompt engineering |
| AI | Retrieval quality (NDCG@10) | > 8 | 7.5 | Amber | AI Search logs | Optimize chunking strategy and embeddings |
| AI | Token consumption (M/day) | Budget dependent | 29.3 | Green | OpenAI usage / billing | Review model routing and prompt efficiency |
| AI | Prompt effectiveness score | > 8 | 9.0 | Green | User feedback / CSAT | Continue prompt optimization iterations |
| Business | DAU | > 1000 | 2311 | Green | API gateway / Entra ID usage | Track rollout success and adoption growth |
| Business | CSAT | > 8 | 8.3 | Green | Feedback API | Tune model responses for improved satisfaction |
| Business | Automation savings (FTE hrs/mo) | > 200 | 336 | Green | Workflow analytics | Validate ROI and scale the automation scope |
| Business | Conversion / resolution improvement (%) | > 95 | 98.0 | Green | CRM and operational analytics | Continue monitoring business impact |

---

## Internal IT Support Copilot

| Category | Metric | Target | Current | Status | Track | Action |
| --- | --- | --- | --- | --- | --- | --- |
| Infrastructure | CPU utilization (%) | > 95 | 85.3 | Amber | Azure Monitor (AKS metrics) | Scale pods and review capacity settings |
| Infrastructure | Memory usage (%) | > 95 | 90.8 | Amber | Azure Monitor | Adjust pod memory or scale cluster resources |
| Infrastructure | Network throughput (MB/s) | > 8 | 8.1 | Green | Azure Network Watcher | Continue monitoring network performance |
| Infrastructure | Availability (%) | > 95 | 96.8 | Green | Application Insights SLA | Keep incident readiness active |
| Application | API latency (ms) | < 800 | 1059 | Amber | Application Insights | Improve prompt routing and retrieval efficiency |
| Application | Error rate (%) | < 2 | 1.5 | Green | Azure Monitor logs | Investigate root causes for failed requests |
| Application | Throughput (req/sec) | > 8 | 8.9 | Green | Application Insights | Maintain autoscaling and load balancing |
| Application | Cold start time (s) | < 8 | 8.3 | Green | App telemetry / AKS startup logs | Keep warm pools and optimize startup behavior |
| AI | Hallucination rate (%) | < 2 | 0.9 | Green | Feedback loops | Continue model and prompt tuning |
| AI | Retrieval quality (NDCG@10) | > 8 | 8.9 | Green | AI Search logs | Keep search performance optimized |
| AI | Token consumption (M/day) | Budget dependent | 42.4 | Green | OpenAI usage / billing | Review cost efficiency periodically |
| AI | Prompt effectiveness score | > 8 | 9.3 | Green | A/B testing results | Continue prompt experimentation |
| Business | DAU | > 1000 | 1779 | Green | API gateway / Entra ID logs | Track growth and user engagement |
| Business | CSAT | > 8 | 8.5 | Green | Feedback API | Continue model behavior tuning |
| Business | Automation savings (FTE hrs/mo) | > 200 | 760 | Green | Workflow analytics | Validate continued ROI |
| Business | Conversion / resolution improvement (%) | > 95 | 93.1 | Amber | CRM / analytics | Investigate process or UX gaps affecting conversions |

---

## Automated Onboarding Assistant

| Category | Metric | Target | Current | Status | Track | Action |
| --- | --- | --- | --- | --- | --- | --- |
| Infrastructure | CPU utilization (%) | > 95 | 97.0 | Green | Azure Monitor (AKS metrics) | Continue scaling plan review |
| Infrastructure | Memory usage (%) | > 95 | 95.7 | Green | Azure Monitor | Monitor memory trends and scale as needed |
| Infrastructure | Network throughput (MB/s) | > 8 | 8.5 | Green | Azure Network Watcher | Ensure network capacity remains healthy |
| Infrastructure | Availability (%) | > 95 | 99.1 | Green | Application Insights SLA | Maintain operational response readiness |
| Application | API latency (ms) | < 800 | 607 | Green | Application Insights | Keep optimizing prompt and retrieval latency |
| Application | Error rate (%) | < 2 | 3.3 | Amber | Azure Monitor logs | Investigate error spikes and rollback paths |
| Application | Throughput (req/sec) | > 8 | 8.8 | Green | Application Insights | Continue capacity planning |
| Application | Cold start time (s) | < 8 | 7.9 | Amber | App telemetry / AKS startup logs | Maintain warm pools and startup optimization |
| AI | Hallucination rate (%) | < 2 | 1.1 | Green | Feedback loops | Continue fine-tuning prompts and RAG quality |
| AI | Retrieval quality (NDCG@10) | > 8 | 9.5 | Green | AI Search logs | Continue improving semantic retrieval |
| AI | Token consumption (M/day) | Budget dependent | 10.8 | Green | OpenAI usage / billing | Maintain cost awareness and routing efficiency |
| AI | Prompt effectiveness score | > 8 | 8.7 | Green | A/B testing | Continue prompt versioning and updates |
| Business | DAU | > 1000 | 3897 | Green | API gateway / Entra ID logs | Track adoption and engagement growth |
| Business | CSAT | > 8 | 9.5 | Green | Feedback API | Continue tracking sentiment |
| Business | Automation savings (FTE hrs/mo) | > 200 | 960 | Green | Workflow analytics | Validate ongoing ROI |
| Business | Conversion / resolution improvement (%) | > 95 | 97.4 | Green | CRM / analytics | Maintain improvement momentum |

---

## Compliance Document Analyzer

| Category | Metric | Target | Current | Status | Track | Action |
| --- | --- | --- | --- | --- | --- | --- |
| Infrastructure | CPU utilization (%) | > 95 | 89.6 | Amber | Azure Monitor (AKS metrics) | Scale pods and review capacity planning |
| Infrastructure | Memory usage (%) | > 95 | 90.2 | Amber | Azure Monitor | Adjust cluster memory allocation |
| Infrastructure | Network throughput (MB/s) | > 8 | 9.3 | Green | Azure Network Watcher | Continue monitoring network health |
| Infrastructure | Availability (%) | > 95 | 95.5 | Green | Application Insights SLA | Keep operational response procedures active |
| Application | API latency (ms) | < 800 | 1135 | Amber | Application Insights | Optimize model routing and retrieval performance |
| Application | Error rate (%) | < 2 | 1.5 | Green | Azure Monitor logs | Investigate error trends for stability |
| Application | Throughput (req/sec) | > 8 | 7.4 | Amber | Application Insights | Review autoscaling and request routing |
| Application | Cold start time (s) | < 8 | 9.4 | Green | App telemetry / AKS startup logs | Keep warm pools and optimize startup times |
| AI | Hallucination rate (%) | < 2 | 1.6 | Green | Feedback loops | Continue prompt and retrieval tuning |
| AI | Retrieval quality (NDCG@10) | > 8 | 9.4 | Green | AI Search logs | Continue search optimizations |
| AI | Token consumption (M/day) | Budget dependent | 24.4 | Green | OpenAI usage / billing | Maintain cost efficiency reviews |
| AI | Prompt effectiveness score | > 8 | 8.5 | Green | A/B testing | Continue prompt improvement cycles |
| Business | DAU | > 1000 | 2161 | Green | API gateway / Entra ID logs | Track adoption and retention |
| Business | CSAT | > 8 | 8.0 | Green | Feedback API | Use feedback to refine behavior |
| Business | Automation savings (FTE hrs/mo) | > 200 | 729 | Green | Workflow analytics | Validate ROI and process automation |
| Business | Conversion / resolution improvement (%) | > 95 | 89.6 | Amber | CRM / analytics | Investigate end-to-end process bottlenecks |

---

## Observations

- Reducing API latency and improving retrieval quality are the top operational priorities for the RAG Knowledge Base and Compliance Document Analyzer.
- Cold start and error-rate optimization are the current improvement areas for onboarding and application workloads.
- Business adoption and automation ROI are strong across all initiatives; the remaining risk is operational performance and model grounding.

