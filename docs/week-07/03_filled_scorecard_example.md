# Filled Example — Evaluation Scorecard (GenAI Contract Risk Analyzer)

## A) Use-Case Metadata

- Use case name: GenAI Contract Risk Analyzer
- Use case ID: genai-contract-risk-analyzer
- Tier (1/2/3): Tier 2
- Environment (dev/pilot/prod): Pilot
- Reviewer(s): AIPO + Risk + Legal SME (example)
- Date: 2026-02-20
- Version (scorecard): v1.0

---

## B) Evidence Maturity Scale (Reminder)

- Self-Assessed
- Documentation-Backed
- Test/Artifact-Backed
- Third-Party Verified

---

## C) Dimension Scores (0–5) + Evidence Maturity (Example)

> Scores below illustrate a realistic “Pilot with Controls” posture. Replace with your actual values and evidence links.

| # | Dimension | Score (0–5) | Evidence Maturity | Rationale (1–2 lines) | Evidence Link / Ref |
|---|----------|-------------|-------------------|------------------------|---------------------|
| 1 | Business Value & ROI | 4 | Documentation-Backed | High legal review effort; strong potential cycle-time reduction. | Pilot business case doc |
| 2 | Risk & Compliance Exposure | 3 | Documentation-Backed | Decision-influencing; controlled by HITL; still requires clear disclaimers. | Risk notes + SOP |
| 3 | Reliability & Determinism | 3 | Test/Artifact-Backed | Acceptable stability with defined manual fallbacks; sampling shows occasional misses. | Pilot QA sampling |
| 4 | Governance & Auditability | 3 | Documentation-Backed | Logging + evidence capture defined; replayability partially proven. | Logging spec |
| 5 | Security & Data Handling | 4 | Test/Artifact-Backed | RBAC and encryption implemented; DLP rules configured for pilot. | Security config |
| 6 | Agentic Safety & Control | 4 | Documentation-Backed | No execution; read-only tools; strict HITL with escalation. | Gate checklist |
| 7 | Operational Readiness | 3 | Documentation-Backed | Monitoring defined; runbooks drafted; needs maturity via pilot ops. | Ops runbook |
| 8 | Vendor & Model Sovereignty | 2 | Documentation-Backed | Gateway used; fallback exists as manual mode; multi-provider routing not proven yet. | Gateway design |

---

## D) Tier 2 Weights (Example)

> Replace weights with your official Week 2 weighting matrix values. Must sum to 1.00.

| Dimension | Weight |
|----------|--------|
| 1. Business Value & ROI | 0.18 |
| 2. Risk & Compliance Exposure | 0.16 |
| 3. Reliability & Determinism | 0.14 |
| 4. Governance & Auditability | 0.14 |
| 5. Security & Data Handling | 0.12 |
| 6. Agentic Safety & Control | 0.10 |
| 7. Operational Readiness | 0.08 |
| 8. Vendor & Model Sovereignty | 0.08 |

---

## E) Weighted Score Calculation (Example)

Formula: **Aggregate Score = Σ (Score × Weight)**

| Dimension | Score | Weight | Weighted Contribution |
|----------|------:|-------:|-----------------------:|
| 1 | 4 | 0.18 | 0.72 |
| 2 | 3 | 0.16 | 0.48 |
| 3 | 3 | 0.14 | 0.42 |
| 4 | 3 | 0.14 | 0.42 |
| 5 | 4 | 0.12 | 0.48 |
| 6 | 4 | 0.10 | 0.40 |
| 7 | 3 | 0.08 | 0.24 |
| 8 | 2 | 0.08 | 0.16 |
| **TOTAL** |  | **1.00** | **3.32** |

**Aggregate readiness score (0.0–5.0):** **3.32**

---

## F) Score-Based Recommendation (Readiness)

Threshold mapping:
- 4.0 – 5.0 → Approve (Ready for Production)
- 3.0 – 3.9 → Pilot with Controls (Limited blast radius)
- Below 3.0 → Block / Redesign

**Readiness recommendation:** **Pilot with Controls**

---

## G) Hard Governance Gates (Permission)

Gate checklist outcome: **Pass with conditions**

Conditions (examples):
- Strengthen sovereignty evidence: prove region routing and log sovereignty metadata
- Improve replayability evidence: expand test coverage for sampled cases
- Formalize HITL training for pilot users with SOP and completion record

---

## H) Overall Confidence

- Overall confidence rating: **Medium**
- Why: Several scores are evidence-backed, but sovereignty and full replayability are still maturing.
- Primary evidence gaps (top 3):
  1. Multi-provider fallback proof (if required)
  2. Replay test coverage across contract types
  3. HITL training completion evidence for all pilot users

---

## I) Final Decision (Human Governance Decision)

- Final decision: **Pilot with Controls**
- Decision authority (Tier 2): BO + AIPO + RISK (+ LEGAL where applicable)
- Conditions: restricted pilot scope; mandatory evidence capture; monthly sampling review
- Review cadence: weekly during pilot
- Next review date: 2 weeks from pilot start
