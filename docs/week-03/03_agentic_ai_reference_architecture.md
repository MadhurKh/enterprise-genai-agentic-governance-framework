# Agentic AI Reference Architecture (Tier 2–3)

## Purpose

This reference architecture defines the enterprise design for **Agentic AI** systems that can:

- plan multi-step tasks
- call tools (APIs)
- optionally execute actions within bounded domains

It emphasizes **controlled autonomy**, explicit policy boundaries, and kill-switch capability.

---

## Architecture (Conceptual)

User / Supervisor UI  
↓  
Experience Layer  
- RBAC / Roles  
- Action confirmation UX  
- Escalation UX (SME / Auditor)  

↓  
Agent Orchestration Layer  
- Planner / Router  
- Tool registry  
- Memory (bounded, policy-controlled)  
- State machine (steps + checkpoints)  

↓  
Control Plane (Guardrails) — enforces permission  
- Policy engine (tier-aware)  
- Tool permissions + scopes  
- Schema contracts (inputs/outputs/actions)  
- Rate limits + budgets  
- Kill switch (global + per-agent)  

↓  
Execution Plane  
- LLM calls  
- Tools / Integrations (write actions)  
- External systems (ERP/CRM/CLM/etc.)  

↓  
Evidence + Audit Layer (always-on)  
- Tool-call logs (inputs/outputs)  
- Decision trace + approvals  
- Evidence store + replay  

↓  
Operations Layer (always-on)  
- Observability  
- Incident response  
- Drift/behavior monitoring  
- Control testing (incl. kill-switch drills)  

---

## Agentic Safety Model

### 1) Bounded Autonomy (Required)

Agents operate only within:
- explicit scope (allowed tasks)
- allowed tools
- allowed data classes
- allowed actions (schema-bound)

This prevents open-ended execution and enforces “least privilege by design.”

---

### 2) Checkpoints (Human-in-the-loop)

Tier-driven checkpoints ensure:
- Tier 2: confirmation for “material” steps (configurable by policy)
- Tier 3: mandatory human authorization for out-of-bounds or high-impact actions

The HITL role must be explicit (end-user verification vs SME review vs independent auditor).

---

### 3) Tool Permissions (Least privilege)

Tool access is granted by:
- role
- tier
- policy
- environment (dev/pilot/prod)

Default posture:
- Tier 1: no write tools
- Tier 2: read tools, and tightly controlled write tools (rare, explicitly gated)
- Tier 3: write tools only within pre-authorized and schema-bound boundaries

---

### 4) Kill Switch (Non-negotiable)

A centralized mechanism to:
- halt all tool execution immediately
- freeze the agent loop
- force manual mode

Tier 3 requires:
- tested rollback paths
- regular kill-switch testing (e.g., quarterly red-button drills)

---

## Where Tier 3 Differs (Enterprise Requirements)

Tier 3 systems require:
- independent oversight (AI auditor)
- immutable logs for action execution
- pre-authorization boundaries for any conditional autonomy
- dual-control approval patterns for sensitive actions (optional but recommended)
- strict rollback mechanisms for reversible actions

---

## Conditional Autonomy (Policy-bound, narrow domains)

Tier 3 does not mean “no autonomy ever.” It means:
- no open-ended execution
- autonomy is allowed only within pre-authorized, narrow boundaries

Examples:
- automated refund ≤ $50 with explicit policy and reversible ledger entry
- automated routing of low-risk tickets to queues
- internal state changes that are non-customer impacting

---

## Failure Modes and Safe Degradation

Agentic systems must support:
- provider outage → manual mode
- tool failure → step rollback or halt + escalation
- confidence drop / anomaly → halt + human checkpoint
- policy violation attempt → deny + log + alert

---

## Governance Mapping (Week 1–2 → Architecture)

Tier classification determines:
- checkpoint frequency
- tool scopes
- logging strictness
- kill-switch requirements

Hard gates are implemented in the Control Plane:
- autonomy boundaries gate
- human oversight gate
- auditability gate
- sovereignty fallback gate
- security baseline gate
