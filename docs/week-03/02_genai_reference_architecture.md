# GenAI Reference Architecture (Tier 1–2 Baseline)

## Purpose

This reference architecture defines the standard enterprise design for **GenAI applications** where the system produces:

- information, summaries, drafts, classifications, or recommendations
- without autonomous execution authority (Tier 1–2)

It maps governance requirements to enforceable technical controls and establishes a baseline that can scale.

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
- LLM Provider (external/internal)  
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
- Model calls (external API / internal model)
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
  - provider outage
  - hallucination spike
  - data leakage suspicion
- Change control:
  - prompt version approvals
  - model version upgrades
  - retrieval index refresh governance

---

## Governance Mapping (Week 1–2 → Architecture)

### Risk Tier enforcement
- Tier 1: lighter controls; still must be safe and auditable for enterprise
- Tier 2: structured outputs and mandatory review checkpoints for decision-impacting outputs

### Hard gates (Week 2)
- Human oversight enforcement is implemented in Experience + Orchestration
- Auditability is implemented through Evidence + Audit Layer
- Vendor sovereignty is implemented via abstraction + fallback (Execution + Ops)

---

## Tier 2 “Pilot with Controls” baseline checklist

A Tier 2 pilot must have:
- RBAC + access control
- Prompt template versioning
- Structured outputs with schema validation
- Defined manual fallback runbook
- Audit trail for material decisions
- Monitoring and basic alerting

If any are missing, outcome should be **Block / Redesign** until addressed.
