# Evaluation Scorecard (Template)

## How to Use

1. Confirm **Tier** (Week 1 classification).
2. Score each dimension **0–5** using Week 2 anchors.
3. Record **Evidence Maturity** for each score (self-assessed vs verified).
4. Apply the **tier-specific weights** (Week 2 weighting matrix).
5. Compute the **weighted aggregate readiness score**.
6. Apply **hard governance gates** (Week 2/Week 5 gate checklist).  
   If any gate fails → **Block / Redesign** regardless of score.

**Note:** Scores represent the current state. Evidence maturity indicates how defensible each score is in audit.

---

## A) Use-Case Metadata

- Use case name:
- Use case ID:
- Tier (1/2/3):
- Environment (dev/pilot/prod):
- Reviewer(s):
- Date:
- Version (scorecard):

---

## B) Evidence Maturity Scale (Confidence Indicator)

Use one of the following for each dimension:

- **Self-Assessed:** judgement-based; not yet backed by artifacts
- **Documentation-Backed:** supported by internal documentation / screenshots / configs / runbooks
- **Test/Artifact-Backed:** supported by executed test results (e.g., replay test, circuit breaker test, monitoring evidence)
- **Third-Party Verified:** validated by independent function or external party (e.g., pen-test report, audit review)

---

## C) Dimension Scores (0–5) + Evidence Maturity

| # | Dimension | Score (0–5) | Evidence Maturity (select one) | Rationale (1–2 lines) | Evidence Link / Ref |
|---|----------|-------------|--------------------------------|------------------------|---------------------|
| 1 | Business Value & ROI |  |  |  |  |
| 2 | Risk & Compliance Exposure |  |  |  |  |
| 3 | Reliability & Determinism |  |  |  |  |
| 4 | Governance & Auditability |  |  |  |  |
| 5 | Security & Data Handling |  |  |  |  |
| 6 | Agentic Safety & Control |  |  |  |  |
| 7 | Operational Readiness |  |  |  |  |
| 8 | Vendor & Model Sovereignty |  |  |  |  |

---

## D) Weights (Tier-Specific)

> Use the weights from `docs/week-02/05_weighting_matrix.md`.

Fill in the weights below (must sum to 1.00):

| Dimension | Weight |
|----------|--------|
| 1. Business Value & ROI |  |
| 2. Risk & Compliance Exposure |  |
| 3. Reliability & Determinism |  |
| 4. Governance & Auditability |  |
| 5. Security & Data Handling |  |
| 6. Agentic Safety & Control |  |
| 7. Operational Readiness |  |
| 8. Vendor & Model Sovereignty |  |

---

## E) Weighted Score Calculation

Formula:  
**Aggregate Score = Σ (Dimension Score × Weight)**

| Dimension | Score | Weight | Weighted Contribution |
|----------|------:|-------:|-----------------------:|
| 1 |  |  |  |
| 2 |  |  |  |
| 3 |  |  |  |
| 4 |  |  |  |
| 5 |  |  |  |
| 6 |  |  |  |
| 7 |  |  |  |
| 8 |  |  |  |
| **TOTAL** |  | **1.00** | **(0.0 – 5.0)** |

**Aggregate readiness score (0.0–5.0):** _______

---

## F) Score-Based Recommendation (Readiness)

> Use Week 2 thresholds.

- 4.0 – 5.0 → Approve (Ready for Production)
- 3.0 – 3.9 → Pilot with Controls (Limited blast radius)
- Below 3.0 → Block / Redesign

**Readiness recommendation:** Approve / Pilot with Controls / Block

---

## G) Hard Governance Gates (Permission)

Complete the gate checklist:  
`04_hard_governance_gates_checklist.md`

**Gate outcome:** Pass / Fail

If fail:
- Which gate(s):
- Required remediation (P0):
- Target date:
- Owner:

---

## H) Overall Confidence (Optional but Recommended)

This reflects whether the **overall score** is defensible.

- Overall confidence rating: Low / Medium / High
- Why: (1–2 lines)
- Primary evidence gaps (top 3):
  1.
  2.
  3.

---

## I) Final Decision (Human Governance Decision)

Final decision remains a **human governance decision**, supported—but not dictated—by score.

- Final decision: Approve / Pilot with Controls / Block & Redesign
- Decision authority (per tier):
- Conditions (if Pilot):
- Review cadence:
- Next review date:
