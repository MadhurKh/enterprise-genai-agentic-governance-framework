# GenAI Reference Architecture (Tier 1–2 Baseline)

## Purpose

This reference architecture defines the standard enterprise design for **GenAI applications** where the system produces:

- information, summaries, drafts, classifications, or recommendations
- without autonomous execution authority (Tier 1–2)

It maps governance requirements to enforceable technical controls and establishes a baseline that can scale into Tier 2/3 deployments.

---

## Architecture (Conceptual)

User / Client App  
↓  
Experience Layer  
- UI / API Gateway  
- AuthN/AuthZ (RBAC)  
- Disclosure + Consent  

↓  
Orchestration Layer  
- Prompt templates + versioning  
- Retrieval (RAG) / tools (read-only)  
- Output structuring (JSON schemas)  
- Policy-aware routing (by tier)  

↓  
Execution Plane  
- **Internal Model Gateway (Sovereignty Abstraction Layer)**  
  - Provider abstraction (no direct vendor calls from app code)  
  - Region routing (EU-only, etc.)  
  - Model selection + version pinning  
  - Fallback logic and failover (secondary model / manual mode)  
  - Audit metadata emission (provider, region, version)  
- LLM Provider(s) (external/internal; behind gateway)  
- Vector DB / Search  
- Document store (contracts, knowledge)  

↓  
Evidence + Audit Layer (always-on)  
- Event log schema (immutable / append-only where required)  
- Evidence store (citations, snippets, references)  
- Human decision capture (accept/override/escalate)  

↓  
Operations Layer (always-on)  
- Observability (logs/metrics/traces)  
- Quality monitoring + drift signals  
- Cost controls and rate limits  
- Incident response runbooks  

---

## Why the Internal Model Gateway is Mandatory (EU Enterprise Lens)

In Tier 2/3 systems, application code should not call a provider (e.g., “OpenAI”) directly.

The **Internal Model Gateway** is the sovereignty abstraction layer that enables:

- **Vendor & Model Sovereignty:** switch providers without refactoring core application logic
- **Jurisdictional compliance:** route processing to EU-only endpoints/models when required
- **Resilience:** automatic fallback to a secondary model or manual process when APIs fail
- **Audit defensibility:** capture provider, model version, and region for every high-impact output

---

## Component Responsibilities

### 1) Experience Layer

Responsibilities:
- Authentication and authorization (RBAC)
- User identity, role, and purpose-of-use
- Disclosures (AI-assisted), consent capture (where applicable)
- Input constraints (file types, size, redaction prompts)

Key enforcement points:
- Block access for unauthorized roles
- Require explicit user confirmation for sensitive outputs (Tier 2)

---

### 2) Orchestration Layer

Responsibilities:
- Prompt template library (versioned)
- Retrieval (RAG) with enterprise-approved sources
- Context assembly: instructions + evidence + user inputs
- Output formatting using **schema contracts**
- Tier-aware rules (Tier 1 vs Tier 2)
- Safety filters (content/PII boundaries)

Key enforcement points:
- Never allow “free-form tool execution”
- Require structured outputs for decision-impacting use cases
- Enforce max context, max tool calls, and deterministic fallbacks

---

### 3) Execution Plane

Responsibilities:
- **Internal Model Gateway (Sovereignty Abstraction Layer)**:
  - provider abstraction (no direct vendor calls)
  - region routing and residency constraints
  - model selection and version pinning
  - fallback logic and outage handling
  - emission of sovereignty metadata for audit
- Retrieval calls to vector DB / search index
- Document ingestion pipeline (optional):
  - scanning/redaction
  - chunking/embeddings
  - metadata tagging (classification, retention class)

Key enforcement points:
- Data minimization: send only required context to model
- Regional routing (EU processing/residency needs)
- Provider abstraction (avoid hard coupling)

---

### 4) Evidence + Audit Layer (Always-on)

Responsibilities:
- Persist inputs (redacted identifiers), prompts/templates, outputs, and evidence references
- Capture human decisions:
  - accepted
  - overridden
  - escalated to SME
- Enable replayability (reconstruct what happened and why)

Key enforcement points:
- Logs must be immutable / append-only for high-risk flows
- Evidence should be stored as references + hashes where possible (avoid raw dumps)
- Access to evidence must be role-controlled (end-user vs SME vs auditor)

---

### 5) Operations Layer (Always-on)

Responsibilities:
- Monitoring:
  - latency/timeouts
  - error rates
  - token usage and cost
  - output anomaly indicators
- Incident response runbooks:
  - provider outage (gateway failover)
  - hallucination spike
  - data leakage suspicion
- Change control:
  - prompt version approvals
  - model version upgrades (via gateway)
  - retrieval index refresh governance

---

## Governance Mapping (Week 1–2 → Architecture)

### Risk Tier enforcement
- Tier 1: lighter controls; still must be safe and auditable for enterprise
- Tier 2: structured outputs and mandatory review checkpoints for decision-impacting outputs

### Hard gates (Week 2)
- Human oversight enforcement is implemented in Experience + Orchestration
- Auditability is implemented through Evidence + Audit Layer
- Vendor sovereignty is implemented via the **Internal Model Gateway** + fallback (Execution + Ops)

---

## Tier 2 “Pilot with Controls” baseline checklist

A Tier 2 pilot must have:
- RBAC + access control
- Prompt template versioning
- Structured outputs with schema validation
- Defined manual fallback runbook
- Audit trail for material decisions
- Monitoring and basic alerting
- **Internal Model Gateway in front of any model provider calls**

If any are missing, outcome should be **Block / Redesign** until addressed.
