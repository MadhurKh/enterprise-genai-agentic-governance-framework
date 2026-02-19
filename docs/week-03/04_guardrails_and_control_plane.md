# Guardrails and Control Plane (Technical Enforcement Layer)

## Purpose

The Control Plane is the **technical enforcement layer** that translates governance policy into runtime constraints.

It prevents “policy-only governance” by ensuring:
- tools cannot be invoked without permission
- outputs cannot bypass schema rules
- autonomy cannot exceed tier boundaries
- audit capture is always-on

---

## Control Plane Components

### 1) Policy Engine (Tier-aware)
A central policy service that evaluates:

- risk tier (Tier 1/2/3)
- user role (end-user, SME, auditor)
- data class (public/internal/confidential/PII)
- allowed tools/actions (scopes)
- environment (dev/pilot/prod)

**Output:** Allow / Deny / Allow-with-conditions (e.g., require approval)

Recommended approach: policy-as-code (OPA-style) but implementation can vary.

---

### 2) Tool Registry + Permissions
A registry describing every tool the system can call:

- tool name
- purpose
- input schema
- output schema
- risk level
- required approvals
- rollback strategy
- data classes allowed

Permissions enforce least privilege:
- Tier 1: no write tools
- Tier 2: read tools; write tools only with explicit approval gates (rare)
- Tier 3: write tools allowed only with policy-bound and schema-bound constraints

---

### 3) Schema Contracts (Structured Enforcement)
All material outputs and tool calls must be schema-validated:

- model output schema (JSON contract)
- tool input schema
- tool output schema
- evidence schema (citations / references)

If schema validation fails:
- retry with constrained prompt
- degrade to manual mode
- log failure and escalate if repeated

---

### 4) Budget and Rate Controls
Enterprise controls for:
- max tokens per request
- max tool calls per session
- max cost per workflow
- timeouts and circuit breakers
- concurrency limits by tier/role

---

### 5) Human Oversight Enforcement (HITL Controls)
Enforces:
- required checkpoints by tier
- defined roles:
  - end-user verification
  - SME review (sampling or escalation)
  - independent AI auditor (Tier 3 governance)

Controls include:
- explicit approval UI/step
- dual-control approvals for sensitive actions (optional)
- forced “review required” state if gate conditions are triggered

---

### 6) Kill Switch (Mandatory)
Two levels:

1) **Global kill switch:** shuts down tool execution platform-wide
2) **Use-case kill switch:** disables a specific agent or workflow

Tier 3 requires:
- tested rollback paths
- regular kill-switch drills (e.g., quarterly)

---

## Control Plane Enforcement Flow (Runtime)

1) Request enters Experience Layer (RBAC, user role, consent)
2) Orchestrator builds plan / prompt
3) Before any tool call or action:
   - policy evaluation occurs
   - schema validation occurs
4) If allowed:
   - execution proceeds
5) If conditional:
   - human approval checkpoint is triggered
6) Every step writes to Evidence + Audit Layer

---

## Minimum Technical Controls by Tier (Summary)

### Tier 1
- RBAC
- prompt template versioning
- output schema validation (recommended)
- basic logging

### Tier 2
- schema validation required for decision-impacting outputs
- evidence capture (citations/inputs)
- manual fallback runbook
- monitoring + alerts baseline

### Tier 3
- policy engine mandatory
- tool registry + least privilege mandatory
- immutable audit logs for actions
- kill-switch + quarterly drills
- independent AI auditor oversight
- rollback mechanisms for reversible actions

---

## Testing Requirements (Control Assurance)

Controls must be testable, not assumed.

Recommended tests:
- policy regression tests (allow/deny cases)
- schema contract tests (valid/invalid payloads)
- tool permission tests (least privilege)
- kill-switch drill simulation
- outage simulation (provider failure → manual mode)
