# Dimension Weighting Matrix

## Purpose
This matrix defines how each evaluation dimension contributes to the final **Aggregate Readiness Score**. Weights are shifted based on the Risk Tier to ensure safety and compliance for higher-risk use cases.

---

## Weighting Distribution (%)

| Dimension | Tier 1 (Assistive) | Tier 2 (Support) | Tier 3 (Execution) |
| :--- | :---: | :---: | :---: |
| 1. Business Value & ROI | 40% | 20% | 10% |
| 2. Risk & Compliance | 10% | 15% | 20% |
| 3. Reliability & Determinism | 10% | 15% | 15% |
| 4. Governance & Auditability | 10% | 10% | 15% |
| 5. Security & Data Handling | 10% | 15% | 15% |
| 6. Agentic Safety & Control | 5% | 10% | 10% |
| 7. Operational Readiness | 10% | 10% | 10% |
| 8. Vendor Sovereignty | 5% | 5% | 5% |
| **TOTAL** | **100%** | **100%** | **100%** |

---

## Weighting Logic Rationale

- **Tier 1:** Focuses heavily on **Business Value** (40%) because the safety risks are inherently low.
- **Tier 3:** Focuses heavily on **Risk, Governance, and Security** (combined 50%). Even a project with infinite ROI cannot pass if its safety and compliance scores are low.
- **Agentic Safety:** Weighting increases as the AI moves from a simple summarizer (Tier 1) to an active agent (Tier 3).