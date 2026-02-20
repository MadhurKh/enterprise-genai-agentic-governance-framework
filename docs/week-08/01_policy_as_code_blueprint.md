# Week 8 — Implementation Blueprint: Policy-as-Code (OPA-style)

## Purpose

Week 8 converts governance **policy statements** into **enforceable technical rules**.  
This file defines the **Policy-as-Code** approach for GenAI and Agentic AI systems, aligned to:

- Tier-based governance (Tier 1/2/3)
- Hard governance gates (permission)
- Tool permissions and bounded autonomy
- Evidence requirements and auditability
- Sovereignty rules (residency + provider constraints)

This is intentionally **vendor-agnostic** and written as an enterprise blueprint.  
Teams may implement it using **OPA/Rego**, **custom policy engines**, or **gateway middleware**.

---

## Policy-as-Code: Core Concept

Policy-as-code means:

- policies are machine-enforceable rules, not PDFs
- enforcement happens **at runtime**, not only at review time
- policy decisions are logged as **audit evidence**

The policy engine evaluates each request and produces a decision:

- **allow** (continue)
- **allow_with_controls** (continue with required controls)
- **deny** (block / degrade to safe fallback)

---

## Where Policy Enforcement Lives

Policy checks should execute at these points:

1. **Before execution** (pre-flight)
   - Tier routing
   - data classification gates
   - tool permissions
   - sovereignty constraints
   - required human oversight presence

2. **During execution** (in-flight)
   - schema validation for tool calls and outputs
   - bounded autonomy checks
   - circuit breaker rules (auto-trip)

3. **After execution** (post-flight)
   - evidence completeness
   - logging + redaction confirmation
   - user action capture (accept/override)
   - replayability metadata capture

---

## Policy Inputs (Required Context)

The policy engine requires a standard input payload.  
This is a **policy input contract**; implementers should standardize it.

### Policy Input Contract (conceptual)

- **use_case_id**
- **tier** (1/2/3)
- **environment** (dev/pilot/prod)
- **user** (id, role, org)
- **data_classification** (public/internal/confidential/restricted)
- **region_requirement** (EU-only / US-only / global / client-specific)
- **requested_tools**
  - tool_name
  - permission_type (read/write/execute)
  - target_system
  - transaction_limit (if applicable)
- **model_request**
  - purpose (summarize/classify/recommend/execute)
  - output_schema_id
- **controls_declared**
  - hitl_mode (none / end_user / sme_review / independent_auditor)
  - audit_logging_enabled (true/false)
  - redaction_enabled (true/false)
  - circuit_breaker_enabled (true/false)
  - model_gateway_enabled (true/false)
- **risk_flags**
  - regulated_domain (true/false)
  - decision_impacting (true/false)
  - autonomous_execution (true/false)

---

## Policy Outputs (Decision Object)

The policy engine returns:

- **decision:** allow | allow_with_controls | deny
- **reason_codes:** list of rule hits
- **required_controls:** list of controls to enforce
- **degrade_mode:** none | manual_mode | read_only_mode | limited_scope
- **evidence_requirements:** what must be logged for audit

---

## Tier Policy Baselines

### Tier 1 (Assistive / Low Risk)

Allowed:
- read-only retrieval
- drafts, summaries, classifications
- no high-impact decisions without explicit user verification

Mandatory:
- RBAC
- disclosure + consent (where required)
- minimum logging (non-sensitive metadata)
- schema validation for structured outputs (where used)

Denied:
- write tools affecting systems of record
- autonomous execution
- high-risk data without approved handling

---

### Tier 2 (Decision Support / Medium Risk)

Allowed:
- recommendations influencing decisions
- read-only retrieval + limited tool use (non-executing)

Mandatory:
- HITL (end-user verification) + SME sampling plan (recommended)
- audit logging + evidence capture
- internal model gateway (sovereignty abstraction)
- circuit breaker enabled
- structured outputs for key objects (risk findings, obligations)

Denied:
- any tool with write authority (unless reclassified and gated)
- outputs without evidence references for decision-impacting claims

---

### Tier 3 (Decision Execution / High Risk)

Allowed (only with strict constraints):
- conditional autonomy within pre-authorized narrow bounds
  - explicit policy boundaries
  - reversible actions
  - transaction caps (if applicable)

Mandatory (non-negotiable):
- HITL defined as appropriate (end-user + independent oversight)
- independent AI auditor review posture
- auditability + replayability
- internal model gateway
- policy-as-code enforcement on tool calls
- circuit breaker with auto-trip + safe fallback
- quarterly kill-switch drills (operational evidence)

Denied:
- open-ended autonomous execution
- write actions without policy-bound schema and limits
- execution without ownership/accountability metadata

---

## Example Policies (Readable Pseudocode)

These examples are written for clarity. Implementers can translate to OPA/Rego or equivalent.

### Policy 1 — Block autonomous execution without Tier 3 controls

IF tier != 3 AND risk_flags.autonomous_execution == true  
THEN decision = deny  
REASON = "AUTONOMY_REQUIRES_TIER3"

---

### Policy 2 — Require model gateway for Tier 2/3

IF tier in (2,3) AND controls_declared.model_gateway_enabled != true  
THEN decision = deny  
REASON = "MODEL_GATEWAY_REQUIRED"

---

### Policy 3 — Sovereignty (EU-only routing)

IF region_requirement == "EU-only" AND model_request.region != "EU"  
THEN decision = deny  
REASON = "SOVEREIGNTY_REGION_VIOLATION"  
DEGRADE = manual_mode

---

### Policy 4 — Tool permission: no write for Tier 1/2

IF tier in (1,2) AND EXISTS(requested_tools WHERE permission_type == "write")  
THEN decision = deny  
REASON = "WRITE_TOOL_NOT_ALLOWED_FOR_TIER"

---

### Policy 5 — Conditional autonomy boundaries (Tier 3)

IF tier == 3 AND risk_flags.autonomous_execution == true  
THEN require:
- transaction_limit exists AND transaction_limit <= approved_cap
- tool schema validated
- audit logging enabled
- circuit breaker enabled
- human escalation path defined

If any missing -> deny with reason codes.

---

### Policy 6 — Evidence requirement for decision-impacting outputs

IF risk_flags.decision_impacting == true  
THEN require:
- output includes evidence references (citations/snippets)
- output_schema_id present
- logging enabled

Missing -> deny or allow_with_controls (pilot-only).

---

## Logging Policy Decisions (Audit Evidence)

Each policy decision must log:

- policy version + rule set version
- input hash (post-redaction)
- decision, reason codes, required controls
- enforcement outcomes (allowed/denied/degraded)
- user + use case + timestamp

This becomes part of the audit evidence packet (Week 5/6).

---

## Integration Guidance

Minimum recommended integration points:

- API Gateway / Orchestrator: pre-flight checks
- Tool Router: enforce tool allowlists and schemas
- Model Gateway: enforce residency, provider routing, metadata capture
- Output Validator: schema validation + evidence checks
- Logging Pipeline: redaction before immutability

### Fail-Open vs. Fail-Closed (Policy Engine Availability)

Policy enforcement must define behavior when the **Policy Engine itself is unavailable**:

- **Tier 1 (Assistive):** May fail-open *only* for low-risk, read-only behavior, if explicitly approved.
- **Tier 2/3 (Decision Support / Execution):** Must **fail-closed** (deny the request) to prevent un-governed AI execution.
- If fail-open is allowed anywhere, it must be:
  - explicitly documented
  - time-bound (incident window)
  - logged as an exception (Week 6 exception management)
  - monitored with elevated alerting

---

## Implementation Deliverable Checklist

- [ ] Policy input contract standardized
- [ ] Policy decision object standardized
- [ ] Tier baselines codified
- [ ] Sovereignty rules implemented (region + provider)
- [ ] Tool permissions enforced
- [ ] Evidence completeness enforced
- [ ] Policy decisions logged and replayable
