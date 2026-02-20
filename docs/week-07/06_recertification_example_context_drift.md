# Filled Example — Re-Certification Triggered by Context Drift (Tier 3 Pattern)

## Scenario

A governed GenAI system (Tier 3 candidate) is operating under EU-aligned controls.  
No code changes are deployed, but **external context changes** trigger a mandatory out-of-cycle review.

---

## Trigger Event (Context Drift)

Type: **Business Context / Regulatory Change**

Example triggers:
- new regulatory guidance affecting logging retention or explainability expectations
- base model vulnerability disclosed (jailbreak pattern) impacting safety
- residency expectations tightened for a client segment

In this example:
- A new internal legal interpretation requires stricter proof of **EU-only processing** for certain client workflows.
- The system must prove sovereignty metadata and region routing enforcement.

---

## Change Request Record

- Use case name / ID: Example Tier 3 Agentic System
- Current tier: Tier 3
- Environment affected: Pilot
- Change type: Context Drift
- Change description: Require stronger sovereignty audit evidence; update assurance tests for EU-only routing.
- Reason for change: Updated legal/regulatory interpretation
- Owner: AIPO
- Date submitted: 2026-02-20

---

## Context Drift Assessment

- What changed (business/regulatory/environment)?  
  EU-only processing proof requirement strengthened.

- Does this increase decision criticality? **No**
- Does this change impacted user group? **Yes** (regulated client segment)
- Does this change residency or sovereignty expectations? **Yes**
- Does this change acceptable risk posture for the enterprise? **Yes** (tighter compliance posture)

Actions required:
- Re-run Tier classification: **Tier remains 3**
- Re-run scorecard + gates: **Required**
- Update evidence packet: **Required**
- Add/upgrade tests: **Required**

---

## Required Remediation (P0)

1. **Sovereignty metadata enforcement**
   - ensure model output contract logs provider, region, model version for every request
   - add validation that requests cannot be processed outside allowed region

2. **Outage/fallback proof**
   - validate circuit breaker + safe fallback under provider/regional unavailability

3. **Audit packet update**
   - add evidence demonstrating sovereignty compliance (routing tests + logs)

---

## Re-Approval and Sign-Off (Tier 3)

Required:
- Executive Business Owner
- Risk Management
- Legal
- AI Platform Owner
- Independent AI Auditor

Outcome (example):
- Decision: **Continue pilot with added controls**
- Conditions: P0 remediation must be completed within 14 days; auditor sampling required for sovereignty fields
- Next review date: 2 weeks
