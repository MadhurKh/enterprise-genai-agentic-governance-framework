# Week 7 — Starter Kit: Adoption Guide (30/60/90 Days)

## Purpose

Weeks 1–6 define **what** good governance looks like. Week 7 shows **how to adopt it** in an enterprise without creating bottlenecks.

This starter kit is designed to:
- accelerate “POC → Pilot → Production” transitions
- make governance repeatable and auditable
- reduce friction between Business, Engineering, Risk, Legal, and Platform teams

---

## Adoption Principles

1. **Readiness is not permission**  
   Scoring indicates readiness; **hard gates + accountable sign-off** determine permission.

2. **Risk-proportional governance**  
   Tier 1 stays lightweight. Tier 2/3 get stronger controls and evidence.

3. **Design for audit from Day 1**  
   Evidence capture is not “after the fact.” It is part of the product.

4. **Separate duties**  
   Platform executes operational tests; Risk/Auditor validates evidence.

5. **Exceptions are explicit and time-bound**  
   If controls can’t be met, log an exception in the system of record and apply compensating controls.

---

## 30/60/90-Day Rollout Plan

### Day 0–30: Establish the Minimum Viable Governance (MVG)

**Objectives**
- Standardize intake and classification
- Establish decision rights and a working review cadence
- Start collecting evidence artifacts

**Actions**
- Stand up **AI Use-Case Review Board (UCRB)** (weekly)
- Nominate owners for each use case: BO, AIPO, EPO, RISK, LEGAL (Tier 2/3), SME
- Require every new use case to complete:
  - Week 5 Intake Form
  - Week 1 Tier Classification
  - Week 5 Scorecard (with evidence maturity)
  - Week 5 Hard Gates checklist
- Create a central **Exception Register** in a system of record (GRC or Jira SecOps)

**Deliverables**
- A governance calendar (standing weekly UCRB)
- 3–5 pilot candidates classified and scored
- First evidence packets assembled for at least 1 Tier 2 pilot

**Success criteria**
- ≥ 80% of new GenAI use cases have Tier classification + scorecard
- UCRB time-to-decision baseline established

---

### Day 31–60: Operationalize Controls and Assurance

**Objectives**
- Convert “paper governance” into proven controls
- Establish monitoring, redaction, and replay capability for Tier 2/3

**Actions**
- Implement minimum controls by tier (Week 5)
- Enforce **Internal Model Gateway** pattern for Tier 2/3 (sovereignty abstraction)
- Implement:
  - schema validation for outputs/evidence
  - PII redaction before immutable storage
  - replayability tests for sampled decisions
- Start the **Operational Assurance Plan** (Week 6):
  - Tier 2: replay test + fallback simulation + schema tests
  - Tier 3: circuit breaker auto-trip simulation + kill-switch drill scheduling

**Deliverables**
- Tier 2 pilot with complete control evidence and monitoring
- First monthly governance metrics pack (Week 6 KPIs)
- Sampling plan documented (SME + RISK)

**Success criteria**
- Gate pass rate improves vs Day 0–30 baseline
- ≥ 90% of Tier 2 systems have evidence packets that include logging + privacy evidence

---

### Day 61–90: Scale + Institutionalize

**Objectives**
- Make governance sustainable and scalable
- Embed recertification and out-of-cycle triggers
- Prove “safe scale” to leadership

**Actions**
- Establish **AI Risk & Controls Council (ARCC)** (bi-weekly/monthly)
- Introduce:
  - exception expiry tracking and closure process
  - quarterly Tier 3 kill-switch drills (with evidence)
  - out-of-cycle recertification triggers for Tier 3
- Expand governance metrics to executive dashboards:
  - Tier 3 kill-switch drill compliance (target 100%)
  - time-to-remediate block conditions
  - HITL override ratio trends
  - sovereignty violations (target 0)

**Fast-Track Tier 1 (Anti-Bottleneck Control)**
Once the UCRB is stable and scoring consistency is proven:
- **Tier 1 use cases should not consume UCRB capacity by default.**
- Tier 1 may be **auto-approved** or **delegated** to the **AI Product Owner (AIPO)** under predefined guardrails:
  - Tier 1 definition strictly enforced (no decision execution, no sensitive data beyond approved bounds)
  - mandatory intake completeness (lightweight)
  - minimum baseline gates (security, privacy, ownership)
  - monthly portfolio reporting to UCRB for transparency
- Any Tier 1 use case that changes scope, data class, or tool permissions triggers immediate reclassification review.

**Deliverables**
- v1 enterprise policy pack: “how we approve GenAI/Agentic AI”
- Tier 3 readiness package (even if not deployed yet): control plan + assurance plan + evidence structure
- Quarterly governance review memo

**Success criteria**
- 100% Tier 3 systems have current kill-switch drills and circuit breaker tests
- Time from intake → pilot decision meets target SLA (e.g., < 14 days median)

---

## Training and Enablement (Recommended)

### Mandatory training for HITL roles
- what to verify (evidence, citations, schema conformance)
- what not to trust (unsupported claims, missing sources)
- when to escalate (policy breach, uncertainty, high impact)

### Training for Engineering/Platform
- model gateway, fallback patterns, sovereignty metadata
- policy-as-code and schema contracts
- circuit breaker and kill-switch patterns

### Training for Risk/Legal
- tier model, gates, exception handling
- evidence packet interpretation and audit posture

---

## Typical Bottlenecks and How to Avoid Them

- **Bottleneck:** incomplete intake forms  
  **Fix:** gate UCRB review on “intake completeness” checklist.

- **Bottleneck:** unclear sovereignty stance  
  **Fix:** mandate internal model gateway for Tier 2/3; document residency rules.

- **Bottleneck:** audit evidence missing  
  **Fix:** evidence packet is created during pilot, not after.

- **Bottleneck:** exceptions become permanent  
  **Fix:** enforce system-of-record logging + expiry dates + closure tracking.

---

## Starter Kit Files Included

- `02_filled_use_case_intake_example.md`
- `03_filled_scorecard_example.md`
- `04_filled_gates_checklist_example.md`
- `05_exception_register_example.md`
- `06_recertification_example_context_drift.md`
