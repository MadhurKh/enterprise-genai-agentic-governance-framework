# Scorecard and Governance Gates — GenAI Contract Risk Analyzer

## 1. Risk Tier Decision

### Assigned Tier: Tier 2 (Decision Support / Medium Risk)

**Rationale:**
- The system produces **recommendations** (risk scores + flags + suggested remediation), not executions
- It does **not** write back to systems of record
- Outputs can influence legal/contractual interpretation → requires stronger governance than Tier 1
- Human review remains mandatory for any decision-taking or action-taking

---

## 2. Dimension Scorecard (Raw Scores)

Scoring uses the anchors:
- `docs/week-02/02_dimension_scoring_anchors.md`

| # | Dimension | Raw Score (0–5) | Justification Summary |
|---|----------|------------------|-----------------------|
| 1 | Business Value & ROI | 4.0 | Clear value: faster triage, consistent risk detection, reviewer productivity uplift |
| 2 | Risk & Compliance Exposure | 3.0 | Medium exposure due to legal context; mitigated by HITL and recommendation-only posture |
| 3 | Reliability & Determinism | 3.0 | Acceptable baseline with defined manual fallback; needs stronger automated degradation patterns |
| 4 | Governance & Auditability | 4.0 | Strong explainability + evidence mapping concept; needs formalized audit schema |
| 5 | Security & Data Handling | 3.0 | Acceptable baseline for synthetic/anonymized POC; production mapping required |
| 6 | Agentic Safety & Control | 3.0 | Recommendation-only; bounded scope; HITL enforced; no execution authority |
| 7 | Operational Readiness | 3.0 | Basic readiness; needs monitoring, incident response, and controlled change management |
| 8 | Vendor & Model Sovereignty | 2.0 | Vendor dependence exists; fallback is manual and portability is not yet tested |

---

## 3. Weighted Scorecard Calculation (Tier 2)

Tier-specific weights are defined in:
- `docs/week-02/05_weighting_matrix.md`

Applying the Tier 2 weighting matrix:

| Dimension | Raw Score (0–5) | Weight (Tier 2) | Weighted Score |
| :--- | :---: | :---: | :---: |
| 1. Business Value & ROI | 4.0 | 20% | 0.80 |
| 2. Risk & Compliance Exposure | 3.0 | 15% | 0.45 |
| 3. Reliability & Determinism | 3.0 | 15% | 0.45 |
| 4. Governance & Auditability | 4.0 | 10% | 0.40 |
| 5. Security & Data Handling | 3.0 | 15% | 0.45 |
| 6. Agentic Safety & Control | 3.0 | 10% | 0.30 |
| 7. Operational Readiness | 3.0 | 10% | 0.30 |
| 8. Vendor & Model Sovereignty | 2.0 | 5% | 0.10 |
| **TOTAL** |  | **100%** | **3.25 / 5.0** |

**Aggregate Weighted Readiness Score:** **3.25 / 5.0**  
**Score-based outcome:** **Pilot with Controls** (3.0 – 3.9)

---

## 4. Radar Chart (Recommended Visual)

A radar/spider chart is recommended for stakeholder communication because it highlights maturity “dents” at a glance.

**Suggested radar inputs (raw scores):**
- Business Value: 4
- Risk/Compliance: 3
- Reliability: 3
- Auditability: 4
- Security: 3
- Agentic Safety: 3
- Ops Readiness: 3
- Vendor Sovereignty: 2

> Optional: Generate and include this chart in Week 4 assets later (e.g., `docs/week-04/assets/scorecard_radar.png`).

---

## 5. Hard Governance Gates (Permission Check)

Gates are defined in:
- `docs/week-02/03_decision_thresholds_and_gates.md`

| Gate | Status | Rationale |
| :--- | :---: | :--- |
| **1. Human Oversight** | **PASS** | HITL is mandatory for all outputs used in decisions. |
| **2. Autonomy Boundaries** | **PASS** | Recommendation-only; no execution authority; read-only access. |
| **3. Governance & Auditability** | **PASS (IMPROVE)** | Evidence mapping exists; audit schema needs standardization. |
| **4. Vendor & Model Sovereignty** | **PASS (COND)** | Single-provider risk noted; fallback/runbook required and portability testing planned. |
| **5. Security Baseline** | **PASS (BASELINE)** | Synthetic/anonymized data used; production controls required for real data. |

---

## 6. Findings (What the Score Reveals)

- **Strengths:** Business Value and Auditability are comparatively strong.
- **Primary weakness (“dent”):** Vendor & Model Sovereignty is lowest (2.0) → portability and tested fallback are the key maturity gap.
- **Practical implication:** Pilot is acceptable only with explicit controls, documented fallback, and clear audit capture.
