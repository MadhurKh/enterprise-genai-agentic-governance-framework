# AI Use-Case Risk Classification

## Purpose

Not all GenAI and Agentic AI use cases carry the same level of enterprise risk.

This framework classifies AI use cases into **three risk tiers** to ensure that:

- Governance intensity matches business impact
- Human oversight is applied where required
- Autonomous behavior is restricted in high-impact scenarios

---

## Risk Tier Overview

| Risk Tier | Description | Governance Intensity |
|---------|------------|---------------------|
| Tier 1 | Assistive / Low Risk | Light governance |
| Tier 2 | Decision Support / Medium Risk | Controlled governance |
| Tier 3 | Decision Execution / High Risk | Strict governance |

---

## Tier 1 — Assistive / Low Risk

### Definition
AI systems that support human work without directly influencing decisions or transactions.

### Examples
- Document summarization
- Drafting internal content
- Knowledge retrieval
- Ideation support

### Governance Requirements
- Named AI owner
- Basic usage logging
- Explicit non-authoritative disclaimer

### Autonomy
- Assistive only
- No execution authority

---

## Tier 2 — Decision Support / Medium Risk

### Definition
AI systems that recommend or prioritize actions but do not execute them.

### Examples
- Risk flagging
- Compliance alerts
- Contract risk scoring with review
- Prioritization engines

### Governance Requirements
- Mandatory human-in-the-loop
- Explainable or evidence-backed outputs
- Decision audit logs
- Defined confidence thresholds

### Autonomy
- Recommendation only
- No independent execution

---

## Tier 3 — Decision Execution / High Risk

### Definition
AI systems that execute or trigger actions with financial, legal, or regulatory impact.

### Examples
- Automated approvals or denials
- Customer communication without review
- Regulatory determinations
- Contractual decisions

### Governance Requirements (Mandatory)
- Executive business ownership
- Legal and risk sign-off
- Full auditability and traceability
- Kill-switch and rollback mechanisms
- Continuous monitoring

### Autonomy
- Fully autonomous execution is **not permitted**
- Conditional execution with human authorization only

---

## Accountability Rule

Every AI use case must have:

- Named business owner
- Responsible operational team
- Defined escalation authority
- Periodic reclassification cadence

Lack of ownership constitutes a **governance failure**.
