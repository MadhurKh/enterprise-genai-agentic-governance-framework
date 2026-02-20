# Week 11 — Minimum Viable Implementation Walkthrough (Tier 2)

**Goal:** Show how to implement a Tier 2 GenAI system using the framework end-to-end (intake → permission → pilot → ops).

---

## What Tier 2 Means (Reminder)

Tier 2 systems:
- influence decisions (legal/financial/clinical/HR) but do not autonomously execute transactions
- require **HITL**, **auditability**, **sovereignty controls** where applicable, and **circuit breaker safe fallback**

---

## Step-by-Step (Tier 2)

### Step 0 — Confirm Business Context
- Define the business objective (e.g., reduce legal review time by 40%)
- Identify the **non-AI baseline** (manual process, rules engine, keyword search)

**Artifacts**
- Week 5: Use-case intake form

---

### Step 1 — Classify the Use Case (Tiering)
- Apply Week 1 Tier rules
- Record tier and rationale in the SoR (use_case_id, release_id)

**Artifacts**
- Week 1: Risk classification
- Week 5/6: SoR record (GRC / Jira SecOps)

---

### Step 2 — Score the Use Case (Readiness)
- Score 8 dimensions + evidence maturity per dimension
- Compute weighted readiness score (Tier 2 weights)
- Assign overall confidence (based on evidence maturity gaps)

**Artifacts**
- Week 2: scoring model + anchors + weighting matrix
- Week 5: scorecard template

---

### Step 3 — Apply Hard Governance Gates (Permission)
- Complete gates checklist
- If “Pass with conditions,” assign owners and due dates
- Confirm HITL roles + **training record capture**

**Artifacts**
- Week 2/5: gates checklist
- Week 6: exception policy (if needed)

---

### Step 4 — Implement Enforcement Architecture (Minimum)
- Route all calls through **Internal Model Gateway** (no direct vendor calls)
- Capture sovereignty metadata (provider, region, model, version)
- Enable circuit breaker with safe degrade mode (**manual_mode** or **read_only**)

**Artifacts**
- Week 8: gateway + breaker patterns
- Week 10: OpenAPI + routing + runbook

---

### Step 5 — Privacy & Logging (EU Reality)
- Redaction before immutability
- Ensure replayability uses redacted prompts or hashed references
- Ensure correlation_id links policy decision → model call → HITL decision

**Artifacts**
- Week 3: logging + evidence store
- Week 10: JSONL examples (with redaction_summary + correlation_id)

---

### Step 6 — Validate Before Pilot
Minimum tests for Tier 2:
- sovereignty routing tests
- jailbreak attempt tests (block + log)
- redaction tests (no PII in immutable store)
- fallback tests (429 + provider down)

**Artifacts**
- Week 8: validation test plan
- Week 10: SLO/alert examples

---

### Step 7 — Pilot Decision and Controls
- Pilot scope: time-bound, limited population, restricted datasets
- Confirm monitoring dashboards + incident runbooks in place
- Ensure change control triggers (prompt/model/context drift)
- Store the pilot decision as a **release decision record** in the SoR

**Artifacts**
- Week 5: decision thresholds and controls
- Week 6: operating cadence
- Week 7: adoption guide

---

### Step 8 — Create the Audit Packet
- Assemble the evidence index + audit packet template
- Store in evidence repo; link in SoR

**Artifacts**
- Week 5: audit evidence packet template
- Week 9: audit-ready evidence index

---

## Definition of “Ready for Production” (Tier 2)

- Score ≥ threshold (or approved pilot with controls)
- Gates passed (no open P0 gate failures)
- Gateway + sovereignty metadata implemented
- Circuit breaker + safe fallback tested
- Validation tests complete (incl. jailbreak)
- Monitoring and runbooks operational
- Audit packet assembled and linked in SoR
