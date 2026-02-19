# Guardrails and Control Plane (Technical Enforcement Layer)

## Purpose

The Control Plane is the **technical enforcement layer** that translates governance policy into runtime constraints.

It prevents “policy-only governance” by ensuring:
- tools cannot be invoked without permission
- outputs cannot bypass schema rules
- autonomy cannot exceed tier boundaries
- audit capture is always-on
- safety failures can automatically trigger degradation to safe/manual mode

---

## Control Plane Components

### 1) Policy Engine (Tier-aware)

A central policy service that evaluates:
- risk tier (Tier 1/2/3)
- user role (end-user, SME, auditor)
- data class (public/internal/confidential/PII)
- allowed tools/actions (scopes)
- environment (dev/pilot/prod)
- jurisdictional constraints (EU-only, etc.)

**Output:** Allow / Deny / Allow-with-conditions (e.g., require approval)

Recommended approach: policy-as-code (OPA-style), though implementation can vary.

---

### 2) Tool Registry + Permissions

A registry describing every tool the system can call:
- tool name, purpose
- input schema / output schema
- risk level (read vs write)
- required approvals
- rollback strategy
- data classes allowed
- sovereignty constraints (if tool calls external services)

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
- policy decision schema

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
- defined oversight roles:
  - end-user verification
  - SME review (sampling or escalation)
  - independent AI auditor (Tier 3 governance)

Controls include:
- explicit approval UI/step
- dual-control approvals for sensitive actions (optional)
- forced “review required” state if gate conditions are triggered

---

## Kill Switch as a Circuit Breaker (Mandatory)

### Why “Circuit Breaker” framing matters

A manual “Red Button” is necessary but insufficient.

If the system starts failing safety checks, violating policy bounds, or breaching sovereignty constraints, it must be able to **trip automatically** and degrade to a safe state.

### Circuit Breaker Behavior (Minimum)

A Control Plane circuit breaker must support:

- **Automatic trip conditions**
  - repeated schema validation failures
  - repeated policy denials on attempted actions
  - safety filter escalation thresholds
  - provider outage / timeout thresholds (via Internal Model Gateway)
  - anomaly detection triggers (optional but recommended)

- **Trip action**
  - halt tool execution immediately
  - freeze agent loop (if agentic)
  - force manual mode or safe fallback pathway

- **Recovery**
  - controlled reset only after:
    - incident review (Tier 3)
    - mitigation applied (prompt/model/tool change)
    - confirmation test passed

### Manual Red-Button (Still Required)

In addition to automatic circuit breakers:
- a global kill switch must exist
- a use-case-specific kill switch must exist
- Tier 3 requires regular kill-switch testing (e.g., quarterly drills)

---

## Control Plane Enforcement Flow (Runtime)

1) Request enters Experience Layer (RBAC, user role, consent)
2) Orchestrator builds plan / prompt
3) Before any model call, tool call, or action:
   - policy evaluation occurs
   - schema validation rules are enforced
4) If allowed:
   - execution proceeds
5) If conditional:
   - human approval checkpoint is triggered
6) If repeated failures occur:
   - **circuit breaker trips**
   - system degrades to safe/manual mode
7) Every step writes to Evidence + Audit Layer

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
- circuit breaker for repeated failures (recommended)

### Tier 3
- policy engine mandatory
- tool registry + least privilege mandatory
- immutable audit logs for actions
- **automatic circuit breaker + manual red-button**
- kill-switch drills (e.g., quarterly)
- independent AI auditor oversight
- rollback mechanisms for reversible actions

---

## Testing Requirements (Control Assurance)

Controls must be testable, not assumed.

Recommended tests:
- policy regression tests (allow/deny cases)
- schema contract tests (valid/invalid payloads)
- tool permission tests (least privilege)
- circuit breaker trip simulation (auto-trip)
- kill-switch drill simulation (manual)
- outage simulation (provider failure → gateway failover → manual mode)
