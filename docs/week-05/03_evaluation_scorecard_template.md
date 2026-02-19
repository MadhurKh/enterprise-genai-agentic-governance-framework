# Evaluation Scorecard (Template)

## How to Use

1. Confirm **Tier** (Week 1 classification).
2. Score each dimension **0–5** using Week 2 anchors.
3. Apply the **tier-specific weights** (Week 2 weighting matrix).
4. Compute the **weighted aggregate readiness score**.
5. Apply **hard governance gates** (Week 2/Week 5 gate checklist).  
   If any gate fails → **Block / Redesign** regardless of score.

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

## B) Dimension Scores (0–5)

| # | Dimension | Score (0–5) | Rationale (1–2 lines) | Evidence Link / Ref |
|---|----------|-------------|------------------------|---------------------|
| 1 | Business Value & ROI |  |  |  |
| 2 | Risk & Compliance Exposure |  |  |  |
| 3 | Reliability & Determinism |  |  |  |
| 4 | Governance & Auditability |  |  |  |
| 5 | Security & Data Handling |  |  |  |
| 6 | Agentic Safety & Control |  |  |  |
| 7 | Operational Readiness |  |  |  |
| 8 | Vendor & Model Sovereignty |  |  |  |

---

## C) Weights (Tier-Specific)

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

## D) Weighted Score Calculation

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

## E) Score-Based Recommendation (Readiness)

> Use Week 2 thresholds.

- 4.0 – 5.0 → Approve (Ready for Production)
- 3.0 – 3.9 → Pilot with Controls (Limited blast radius)
- Below 3.0 → Block / Redesign

**Readiness recommendation:** Approve / Pilot with Controls / Block

---

## F) Hard Governance Gates (Permission)

Complete the gate checklist:  
`04_hard_governance_gates_checklist.md`

**Gate outcome:** Pass / Fail

If fail:
- Which gate(s):
- Required remediation (P0):
- Target date:
- Owner:

---

## G) Final Decision (Human Governance Decision)

Final decision remains a **human governance decision**, supported—but not dictated—by score.

- Final decision: Approve / Pilot with Controls / Block & Redesign
- Decision authority (per tier):
- Conditions (if Pilot):
- Review cadence:
- Next review date:
