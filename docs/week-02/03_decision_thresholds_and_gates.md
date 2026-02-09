# Decision Thresholds and Hard Governance Gates

## Decision Thresholds (Score-Based)

The aggregate readiness score maps to the following outcomes:

| Aggregate Score | Recommended Outcome |
|-----------------|--------------------|
| **4.0 – 5.0** | **Approve** (Ready for Production) |
| **3.0 – 3.9** | **Pilot with Controls** (Limited blast radius) |
| **Below 3.0** | **Block / Redesign** (Inadequate maturity) |

These thresholds apply **only when all Hard Governance Gates are satisfied**.

---

## Hard Governance Gates (Overriding Gates)

> **Numerical scores measure readiness. Governance gates determine permission.**

Failure of any gate results in **Block / Redesign**, regardless of score.

---

### Gate 1 — Human Oversight Enforcement

**Failure Condition:**  
No clearly defined Human-in-the-Loop role, or oversight is purely reactive for Tier-2 or Tier-3 systems.

---

### Gate 2 — Agentic Autonomy Boundaries

**Failure Condition:**  
Agent has execution authority (state change, transaction, or external action) without explicit policy-bound constraints or supervisory control.

*Technical enforcement of autonomy boundaries is defined in Week 3: Reference Architecture.*

---

### Gate 3 — Governance & Auditability

**Failure Condition:**  
Inability to reconstruct decision logic, prompts, evidence, or ownership for material outcomes.

---

### Gate 4 — Vendor & Model Sovereignty

**Failure Condition:**  
Critical enterprise function relies on a single provider with no tested fallback, exit strategy, or manual override.

---

### Gate 5 — Security & Data Protection

**Failure Condition:**  
Data sensitivity not classified or enterprise security baseline not met.

---

## Re-Evaluation Triggers

Mandatory re-evaluation is required upon:

- Change in autonomy level
- Change in model or vendor
- Expansion of scope or user base
- Incident, audit finding, or regulatory inquiry
