# Week 11 — Minimum Viable Implementation Walkthrough (Tier 3)

**Goal:** Show how to implement a Tier 3 Agentic system using the framework end-to-end (approval → enforcement → drill → audit).

---

## What Tier 3 Means (Reminder)

Tier 3 systems:
- can initiate actions (write access / transactions / workflow execution)
- must be **policy-bound**, **conditionally autonomous**, and **reversible**
- require **fail-closed** governance if enforcement components are unavailable

---

## Step-by-Step (Tier 3)

### Step 0 — Define Autonomy Boundaries
- Translate autonomy boundaries into **Schema Contracts** before development begins (Week 3/8).
  - Define allowed action types, parameter ranges, and “out-of-bounds” escalation contracts.
  - Ensure tool input/output schemas enforce the autonomy envelope.

- What can the agent do autonomously?
- Define **pre-authorized narrow domains** (e.g., refunds ≤ $50)
- Define “Out-of-bounds” escalation path (human authorization)
- Record the autonomy bounds in the SoR

**Artifacts**
- Week 1: tier definition (conditional autonomy)
- Week 8: policy-as-code blueprint
- Week 10: release readiness checklist (Tier 3 section)

---

### Step 1 — Threat Model and Pen-Test
- Create a threat model (prompt injection, tool escalation, data exfiltration, privilege abuse)
- Run penetration testing for the orchestration + tool plane
- Store evidence artifacts (report + remediation proof)

**Artifacts**
- Week 9: executive evidence expectations
- Week 10: Tier 3 readiness checklist

---

### Step 2 — Implement Policy-as-Code Enforcement
- Pre-flight: tier gating, tool permissions, sovereignty routing checks
- In-flight: tool allowlists, write constraints, budget/rate thresholds
- Post-flight: evidence capture validation

**Rules**
- If policy engine unhealthy → **fail-closed** (Tier 3)
- Break-glass is permitted only via explicit **SoR record** + time-bound approval

**Artifacts**
- Week 8: policy-as-code blueprint
- Week 10: Rego sample policies

---

### Step 3 — Implement Internal Model Gateway + Sovereignty Abstraction
- No direct vendor calls
- Provider routing + metadata capture
- 429/quota fallback must not violate policy
- Log routing decisions as audit events (with correlation_id)

**Artifacts**
- Week 8/10: gateway pattern + OpenAPI + routing table

---

### Step 4 — Circuit Breaker + Kill Switch
- Auto-trip circuit breaker for:
  - sovereignty breach
  - cost/budget breach
  - safety/jailbreak spikes
  - operational failure spikes
- Manual kill switch for emergencies
- Safe degrade mode for Tier 3 is typically **fail_closed** (unless explicitly authorized otherwise)

**Artifacts**
- Week 10: breaker runbook + alerts/SLOs

---

### Step 5 — Run Kill Switch Drill (Quarterly)
- Execute drill (Platform/Engineering Owner)
- Validate evidence (Independent AI Auditor / Risk)
- Store drill record and time-to-disable metric

**Artifacts**
- Week 6: operational assurance plan
- Week 10: runbook (drill section)

---

### Step 6 — Validate
Tier 3 validation must include:
- jailbreak attempts and tool escalation attempts
- fail-closed behavior when policy engine unavailable
- circuit breaker trip simulation (cost + safety + sovereignty)
- rollback / compensation action tests

**Artifacts**
- Week 8: validation test plan
- Week 10: alerts/SLOs examples

---

### Step 7 — Audit Packet + Evidence Index
- Ensure correlation IDs and decision records are complete
- Exceptions are logged (if any) with compensating controls and expiry
- Store the exception register in the SoR (GRC / Jira SecOps), not as a loose document

**Artifacts**
- Week 5: audit packet template
- Week 9: evidence index
- Week 6/7: exception management pattern

---

## Definition of “Ready for Production” (Tier 3)

- Independent AI Auditor assigned
- Threat model + pen-test complete
- Policy-as-code enforcement deployed (pre/in/post flight)
- Gateway abstraction deployed; sovereignty enforced
- Circuit breaker + manual kill switch implemented and tested
- Quarterly drill evidence current
- Full audit packet assembled and linked to SoR
