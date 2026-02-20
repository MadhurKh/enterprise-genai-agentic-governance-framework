# Filled Example — Hard Governance Gates Checklist (GenAI Contract Risk Analyzer)

## Purpose

This example illustrates how a Tier 2 system can **pass gates** while still being restricted to a controlled pilot.

Overall rule: If any gate fails, outcome is **Block / Redesign**.

---

## Gate 1 — Human Oversight Enforcement

Result: **Pass (with training evidence required)**

Evidence:
- HITL role: End-user verification (legal analyst) + SME sampling review
- Training:
  - SOP published for “how to verify AI outputs”
  - Known failure patterns documented (missing clauses, wrong citations)
  - Escalation criteria documented (high-value/high-risk contracts)

Training completion record:
- Pilot users trained: ___ / ___
- Training date(s): _______
- Training owner: AIPO / Legal Ops

Notes:
- No autonomous action; user must confirm before acting on findings.

---

## Gate 2 — Auditability and Replayability

Result: **Pass (pilot scope)**

Evidence:
- Request metadata logged (user, timestamp, doc id)
- Prompt template version captured
- Output hashes captured
- User action logged (accept/override)

Notes:
- Replay tests sampled for key contract types; expand coverage during pilot.

---

## Gate 3 — Security and Data Protection Baseline

Result: **Pass**

Evidence:
- RBAC enforced; only legal team can access contract uploads
- Encryption in transit/at rest enabled
- DLP rules configured for pilot
- Retention policy defined with redaction rules

Notes:
- Pilot uses synthetic or low-sensitivity contracts first.

---

## Gate 4 — Agentic Autonomy Boundaries (Tier 2–3)

Result: **Pass**

Evidence:
- Read-only tools only (retrieval)
- No write authority
- Output schema validation for structured risk objects

Notes:
- If any write tools are introduced later → immediate reclassification review.

---

## Gate 5 — Sovereignty (Vendor + Jurisdiction)

Result: **Pass with conditions**

Evidence:
- Internal Model Gateway used (no direct vendor calls)
- Residency policy documented (EU-only for EU clients)
- Manual fallback mode defined (non-AI baseline)

Conditions:
- Implement sovereignty metadata logging (provider, region, model version)
- Validate region routing tests for EU-only path

---

## Gate 6 — Circuit Breaker and Kill Switch

Result: **Pass**

Evidence:
- Circuit breaker rules defined:
  - repeated missing evidence/citations
  - repeated policy violations
  - high override rate spike
- Fallback mode: manual review process

Notes:
- Tier 2 does not require quarterly kill-switch drills; still recommended for mature controls.

---

## Gate 7 — Ownership and Accountability

Result: **Pass**

Evidence:
- BO named: Head of Legal Ops (example)
- AIPO named
- EPO named
- Risk and Legal contacts named
- Review cadence defined

---

## Gate Outcome

- Overall result: **Pass**
- Decision recommendation: **Pilot with Controls**
- P0 conditions:
  1. Sovereignty metadata logging
  2. Expanded replay test coverage
  3. HITL training completion record for all pilot users
