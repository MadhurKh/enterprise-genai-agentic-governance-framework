# RUNBOOK.md — GenAI/Agentic System Incident Runbook (Starter Template)

**Purpose:** Provide a standard operational response for AI incidents, aligned with governance controls.

---

## Scope

Applies to:
- Tier 2 decision-support systems
- Tier 3 agentic execution systems

---

## Severity Levels (Example)

- **P0:** sovereignty breach, uncontrolled execution, major security incident
- **P1:** sustained 429/quota exhaustion, major quality regression, repeated breaker trips
- **P2:** isolated errors, minor latency degradation

---

## Immediate Actions

1. Confirm tier and current safe degrade mode
2. If Tier 3 → **fail-closed** unless break-glass authorized (SoR record required)
3. Trip circuit breaker if thresholds violated
4. Disable write tools if any tool escalation suspected
5. Notify stakeholders (AIPO, Risk; Tier 3: Independent AI Auditor)
6. Confirm alerts are firing and dashboards reflect the state

---

## Communications (Minimum)

- Post an incident update to the agreed channel (incident bridge)
- Notify business owner of impact and degrade mode
- For Tier 3: notify ARCC/exec sponsor if user impact is material

---

## Evidence Preservation (Privacy First)

- confirm redaction summary exists before writing immutable evidence
- capture correlation_id chain for incident window
- snapshot policy versions and gateway routing decisions
- store postmortem and remediation evidence in the evidence repo

---

## Recovery Criteria

- root cause identified
- remediation applied and validated
- gates reassessed if changes are material
- recert record stored in the SoR

---

## Postmortem Checklist

- incident narrative and timeline
- what control failed or was missing
- corrective actions with owners/due dates
- new validation test cases added
- confirm whether an exception waiver was used (and log it)
