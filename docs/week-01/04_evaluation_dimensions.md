# Evaluation Dimensions

## Purpose of the Evaluation Framework

Enterprise GenAI and Agentic AI systems must be evaluated on **more than technical performance**.

This framework assesses AI systems across business, risk, governance, and operational dimensions to determine suitability for:

- Enterprise deployment
- Controlled pilot
- Redesign or rejection

---

## Evaluation Dimension Overview

All GenAI and Agentic AI use cases are evaluated across **eight core dimensions**.

| # | Dimension | Primary Focus |
|--|----------|---------------|
| 1 | Business Value & ROI | Quantifiable value and cost-to-value proportionality. |
| 2 | Risk & Compliance Exposure | Legal, regulatory, and reputational impact. |
| 3 | Reliability & Determinism | Output consistency and failure handling. |
| 4 | Governance & Auditability | Decision traceability and ownership clarity. |
| 5 | Security & Data Handling | PII protection and access controls. |
| 6 | Agentic Safety & Control | Bounded autonomy and kill-switches. |
| 7 | Operational Readiness | Monitoring, incident response, and versioning. |
| 8 | Vendor & Model Sovereignty | Reliance on specific providers, API stability, and fallback capability. |

---

## Dimension Definitions

### 1. Business Value & ROI
- **Problem Clarity:** The business problem addressed by the AI system is clearly defined, material, and non-trivial.
- **Value Quantification:** Expected benefits (cost reduction, risk avoidance, efficiency gains, quality improvement) are estimated using reasonable and transparent assumptions.
- **Value Sustainability:** Benefits are expected to persist beyond initial deployment and pilot phases.
- **Cost-to-Value Proportionality:** Implementation, operational, and governance costs are justified relative to the expected value delivered.

---

### 2. Risk & Compliance Exposure
- **Legal & Regulatory Impact:** Identification of applicable regulations, contractual obligations, and compliance requirements.
- **Financial & Reputational Risk:** Assessment of potential financial loss or reputational damage resulting from incorrect or harmful AI outputs.
- **Stakeholder Harm:** Evaluation of possible negative impact on customers, employees, or external stakeholders.
- **Residual Risk Awareness:** Explicit understanding of remaining risk after mitigation controls are applied.

---

### 3. Reliability & Determinism
- **Output Consistency:** Similar inputs produce stable, predictable, and repeatable outputs.
- **Failure Handling:** Defined behavior for errors, timeouts, missing data, or degraded dependencies.
- **Edge-Case Awareness:** Known limitations, boundary conditions, and confidence thresholds are documented.
- **Dependency Stability:** Resilience to model updates, API changes, or upstream system instability.

---

### 4. Governance & Auditability
- **Decision Traceability:** Ability to reconstruct how and why a specific AI output or action was produced.
- **Evidence & Reasoning Capture:** Storage of prompts, context, rules, policies, or evidence influencing decisions.
- **Ownership Clarity:** Clearly defined accountable owners for AI behavior, outcomes, and exceptions.
- **Review & Re-certification:** Defined process for periodic governance review, re-approval, and risk reassessment.

---

### 5. Security & Data Handling
- **Data Sensitivity Classification:** Clear identification of data types processed (PII, confidential, regulated, or proprietary).
- **Access Controls:** Role-based access management and separation of duties.
- **Data Protection:** Encryption, masking, secure transmission, and protection against unauthorized access.
- **Retention & Deletion:** Defined policies for data storage duration, archival, and secure deletion.

---

### 6. Agentic Safety & Control
- **Bounded Autonomy:** Ensures the agent cannot exceed its explicitly defined scope, authority, or policy constraints.
- **HITL Enforcement:** Mandatory human checkpoints for high-impact, irreversible, or exception-prone steps.
- **Escalation & Kill-Switches:** Immediate manual override capability in case of unexpected or unsafe behavior.
- **Cross-Agent Safety:** Controls to prevent unintended interactions, feedback loops, or escalation across multiple agents.

---

### 7. Operational Readiness
- **Monitoring & Alerting:** Continuous visibility into system health, anomalies, and performance degradation.
- **Incident Response:** Defined procedures for investigation, rollback, remediation, and stakeholder communication.
- **Change & Version Management:** Controlled rollout and rollback of model, prompt, logic, or policy changes.
- **Support Ownership:** Clear responsibility for day-to-day operation, maintenance, and issue resolution.

---

### 8. Vendor & Model Sovereignty
- **Lock-in Risk:** Evaluation of the cost, effort, and feasibility of switching models, providers, or platforms.
- **Sovereignty:** Assessment of where data is processed and stored, and whether model residency aligns with enterprise or regulatory expectations.
- **Provider Stability:** Dependency on vendor uptime, API consistency, commercial terms, and roadmap volatility.
- **Fallback Strategy:** Existence of a secondary model, alternative provider, or manual process if the primary service fails.

---

## Proportionality Reminder

The depth and rigor applied to each dimension must be **proportional to the assigned risk tier**.  
Higher-risk use cases require stronger evidence, controls, and documentation across all dimensions.

---

## Proportionality Principle

- Tier 1 → Lightweight evaluation
- Tier 2 → Structured evaluation
- Tier 3 → Strict, multi-stakeholder evaluation
