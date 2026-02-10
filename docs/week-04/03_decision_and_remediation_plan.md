# Decision and Remediation Plan — GenAI Contract Risk Analyzer

## Final Decision

### Decision: **PILOT WITH CONTROLS** (Tier 2)

**Decision basis:**
- Aggregate weighted readiness score: **3.25 / 5.0** → Pilot range
- Hard governance gates pass, with conditional improvements required
- Risk is acceptable for a controlled pilot because:
  - No execution authority and no write-back
  - Human review is mandatory
  - Synthetic/anonymized data is used in the demo

---

## Pilot Controls (Mandatory Conditions)

The pilot must operate with the following controls:

### 1) Strict Human-in-the-Loop (HITL)
- End-user verification required for all outputs used in decision-making
- No automated approvals, rejections, or external communications

### 2) Restricted Scope (“Limited blast radius”)
- Limited contract types and use cases (e.g., triage + risk flagging)
- Explicit exclusions for edge cases requiring SME review

### 3) Audit Evidence Capture (Minimum Viable Audit Trail)
Persist (at minimum):

- Input identifiers (redacted) and document version
- Prompt template/version and key parameters
- Model/provider identifiers (vendor + model version where available)
- Output (risk score + flags + evidence references)
- Human reviewer action (accept/override) and notes
- Timestamp and user/role

> **Architecture linkage:** The technical mechanism and schema for audit capture will be defined in **Week 3: Reference Architecture** (Audit Log Schema, storage, retention, and access patterns).

### 4) Vendor Failure Playbook
- Manual fallback must be documented and operable
- Define “degraded mode” behavior and escalation path
- Ensure reviewers can complete work without AI dependency

### 5) Security and Data Controls (Pilot Baseline)
- Role-based access for pilot users
- Retention rules for pilot artifacts and logs
- Rules for handling any non-synthetic data (if introduced)

---

## Key Gaps Preventing “Approve” Today

1. **Vendor & Model Sovereignty**
   - Portability and exit strategy not proven
   - Fallback not tested under failure simulation

2. **Operational Readiness**
   - Monitoring and incident response are not production-grade
   - Change/version management for prompts and models needs formalization

3. **Formal Audit Log Schema**
   - Audit intent exists, but schema and retention controls need standardization

4. **Enterprise Security Mapping**
   - Requires alignment to enterprise policy before production use with real contracts

---

## Remediation Plan (Prioritized)

### P0 — Mandatory Before Pilot Launch (Baseline Controls)
1. **Manual Fallback Runbook:** Define manual process if AI API is unavailable.
2. **Audit Schema Finalization:** Implement the Audit Log Schema (Week 3 Architecture) to ensure traceability.
3. **Pilot Scope & Exclusions:** Document allowed contract types and excluded high-stakes scenarios.

### P1 — Required Before Scaling Pilot
1. **Automated Reliability Checks:** Introduce confidence thresholds and “Needs Manual Review” gating for low-confidence outputs.
2. **Monitoring & Alerts:** Error rate, latency, timeouts, and output anomaly monitoring.
3. **Cost Monitoring:** Token usage alerts and cost guardrails.

### P2 — Required for “Approve” (Production Readiness)
1. **Model Portability Testing:** Run the same workflow on an alternative provider/model to reduce lock-in and raise sovereignty maturity.
2. **Governance Review Cadence:** Formalize periodic governance review (Tier 2 cadence).
3. **SME Sampling:** Enable SME audit sampling for higher-impact contract categories.

---

## Re-evaluation Triggers

Mandatory re-evaluation is required if any of the following occur:

- System is granted write-back or transaction authority (risk tier change likely)
- System is used on real (non-anonymized) PII data
- Underlying model/provider changes
- Scope expands materially (new contract types, broader user base)
- Incident, audit finding, or regulatory inquiry occurs
