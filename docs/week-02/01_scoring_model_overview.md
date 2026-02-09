# Scoring Model Overview

## Purpose of the Scoring Model

The purpose of this scoring model is to translate qualitative governance evaluation into a **structured, repeatable, and defensible enterprise decision**.

While the evaluation dimensions define *what* must be assessed, the scoring model defines:

- How readiness is measured (0–5 scale)
- How risks are weighted proportionally based on Risk Tier
- How scores translate into approval outcomes

The model is aligned with **European enterprise governance best practices**, where transparency, proportionality, and auditability are essential.

---

## Scoring Philosophy: Risk-Proportional Weighting

This framework explicitly recognizes that **business value cannot compensate for unacceptable risk** in higher-impact systems.

Accordingly, **risk-proportional weighting** is applied:

- **Tier 1 (Assistive):** Heavily weighted toward *Business Value* and usability
- **Tier 2 (Decision Support):** Balanced weighting across *Value, Reliability, and Governance*
- **Tier 3 (Decision Execution):** Heavily weighted toward *Risk, Security, Agentic Safety, Governance, and Vendor Sovereignty*

Even exceptionally high business value **cannot justify deployment** if Tier-3 governance requirements are not met.

Specific tier-wise weight allocations are defined in the **Dimension Weighting Matrix**:

- `docs/week-02/05_weighting_matrix.md`

---

## Aggregated Score Calculation

The overall readiness score is calculated as:
Σ (Dimension Score × Tier-Specific Weight) = Aggregate Readiness Score (0.0 – 5.0)

The resulting score represents **readiness**, not permission, and is mapped to an explicit enterprise decision **only after all Hard Governance Gates are satisfied**.

---

## Governance Guardrails (Non-Negotiable)

> **A high aggregate score does not override a critical governance failure.**

The following conditions **automatically trigger Block / Redesign**, regardless of total score:

1. Absence of required Human-in-the-Loop oversight for Tier-2 or Tier-3 systems
2. Inability to audit or reconstruct decision logic
3. Unclear business or governance ownership
4. Unbounded or open-ended autonomous execution
5. Critical failure in **Security, Agentic Safety, Governance, or Vendor & Model Sovereignty**

---

## Outcome of the Scoring Model

The scoring model produces:

- An overall readiness score
- A multi-dimensional maturity view (e.g., radar-style assessment)
- A governance decision recommendation:
  - **Approve**
  - **Pilot with Controls**
  - **Block / Redesign**

Final approval remains a **human governance decision**, supported—but never dictated—by the score.
