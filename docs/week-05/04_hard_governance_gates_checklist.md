# Hard Governance Gates Checklist (Permission Layer)

## Purpose

This checklist determines **permission** to deploy (Pilot / Production).  
It overrides numerical readiness scoring.

**Rule:** If any gate fails, the outcome is **Block / Redesign** (Tier 2–3), regardless of aggregate score.

---

## Gate 1 — Human Oversight Enforcement

Requirement:
- HITL role is explicitly defined (end-user vs SME vs auditor)
- approval checkpoints exist where required by tier
- override and escalation are supported and logged
- **HITL competency is ensured** (humans understand what to verify, what not to trust, and when to escalate)

Pass criteria:
- Tier 2: end-user verification exists for decision-impacting outputs
- Tier 3: explicit human authorization for out-of-bounds actions + auditor sampling plan
- **Training and guidance documented** for HITL roles, including:
  - verification checklist or SOP
  - examples of known failure patterns (hallucinations, missing clauses, incorrect citations)
  - escalation criteria
  - completion record (training date, audience, owner)

Result: Pass / Fail  
Evidence ref:  
Notes:

---

## Gate 2 — Auditability and Replayability

Requirement:
- event logging exists (request → prompt → evidence → output → decision)
- evidence references/hashes exist
- model/prompt/tool versions captured

Pass criteria:
- For Tier 2–3, material decisions can be reconstructed from stored artifacts

Result: Pass / Fail  
Evidence ref:  
Notes:

---

## Gate 3 — Security and Data Protection Baseline

Requirement:
- RBAC enforced
- encryption in transit and at rest
- data minimization
- DLP controls where required
- retention policy defined

Pass criteria:
- No uncontrolled PII exposure paths exist

Result: Pass / Fail  
Evidence ref:  
Notes:

---

## Gate 4 — Agentic Autonomy Boundaries (Tier 2–3)

Requirement:
- tools are permissioned (least privilege)
- write actions are schema-bound and policy-bound
- rollback exists for reversible actions (Tier 3)
- unbounded autonomy is prohibited

Pass criteria:
- Tier 3: conditional autonomy only within pre-authorized narrow bounds

Result: Pass / Fail  
Evidence ref:  
Notes:

---

## Gate 5 — Sovereignty (Vendor + Jurisdiction)

Requirement:
- **Internal Model Gateway** used (no direct vendor calls from app code)
- region routing/residency rules enforced where required
- fallback strategy exists and is testable

Pass criteria:
- Provider outage or model change does not break the business function without a fallback

Result: Pass / Fail  
Evidence ref:  
Notes:

---

## Gate 6 — Circuit Breaker and Kill Switch

Requirement:
- manual kill switch exists (global + per-use-case where needed)
- automatic circuit breaker trips on repeated safety/policy failures
- manual mode / safe fallback is defined

Pass criteria:
- Tier 3: kill-switch drill schedule exists and produces audit evidence

Result: Pass / Fail  
Evidence ref:  
Notes:

---

## Gate 7 — Ownership and Accountability

Requirement:
- business owner accountable for outcomes
- AI product owner accountable for governance adherence
- platform owner accountable for runtime controls
- auditor role (Tier 3) defined

Pass criteria:
- all owners explicitly named (not just roles)

Result: Pass / Fail  
Evidence ref:  
Notes:

---

## Gate Outcome

- Overall result: **Pass / Fail**
- If Fail:
  - Required remediation (P0):
  - Owner:
  - Due date:
  - Re-evaluation date:
