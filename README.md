# Enterprise GenAI & Agentic AI Governance and Evaluation Framework

This repository contains a practical, enterprise-ready framework for evaluating, governing, and safely operationalizing **Generative AI (GenAI)** and **Agentic AI** systems.

The framework is aligned with **European enterprise governance best practices**, emphasizing risk proportionality, accountability, auditability, controlled/conditional autonomy, and vendor/model sovereignty—rather than experimental or hype-driven AI adoption.

It is designed for leaders responsible for **owning AI decisions**, not just building AI solutions.

---

## Why This Framework Exists

As GenAI and Agentic AI move from experimentation into core enterprise workflows, organizations face critical questions:

- Which AI use cases are acceptable to deploy?
- How much autonomy is safe—and when?
- What governance controls are mandatory?
- Who is accountable when AI decisions go wrong?
- How do we balance innovation with regulatory and reputational risk?

This framework provides **clear, decision-ready answers** to those questions.

---

## Scope

This framework applies to:

- Enterprise GenAI applications (internal or client-facing)
- Agentic AI systems with bounded or conditional autonomy
- AI systems influencing decisions, recommendations, or execution
- Regulated or high-impact business environments
- Vendor-provided AI services and third-party model integrations

**Out of scope by design:**
- Research-only prototypes
- Academic model benchmarking
- Open-ended consumer chatbots
- Vendor-specific or proprietary implementations

---

## Quick Start (How to Use)

Use this framework as an enterprise decision workflow:

1) **Classify** the use case into Tier 1/2/3 (risk + autonomy posture)  
2) **Score** the use case across the 8 dimensions using anchors  
3) **Compute** the weighted readiness score using the Tier weighting matrix  
4) **Gate** the outcome using hard governance gates (permission overrides)  
5) **Decide**: Approve / Pilot with Controls / Block  
6) **Operationalize** mandatory controls + re-evaluation triggers

---

## Framework Structure

### 📁 Week 1 — Foundation (Completed)

Located under `docs/week-01/`

1. **Scope and Positioning**  
   → `docs/week-01/01_scope_and_positioning.md`

2. **Governance Philosophy**  
   (incl. HITL roles: end-user verification, SME review, independent AI auditor)  
   → `docs/week-01/02_governance_philosophy.md`

3. **AI Use-Case Risk Classification**  
   (Tier 1 Assistive / Tier 2 Decision Support / Tier 3 Decision Execution with conditional autonomy)  
   → `docs/week-01/03_ai_use_case_risk_classification.md`

4. **Evaluation Dimensions**  
   (8 dimensions incl. **Vendor & Model Sovereignty**)  
   → `docs/week-01/04_evaluation_dimensions.md`

5. **Decision & Approval Logic**  
   → `docs/week-01/05_decision_and_approval_logic.md`

6. **Framework Structure & Table of Contents**  
   → `docs/week-01/06_framework_structure_and_toc.md`

---

### 📁 Week 2 — Scoring & Permission Model (Completed)

Located under `docs/week-02/`

1. **Scoring Model Overview**  
   → `docs/week-02/01_scoring_model_overview.md`

2. **Dimension-Level Scoring Anchors**  
   → `docs/week-02/02_dimension_scoring_anchors.md`

3. **Decision Thresholds and Hard Governance Gates**  
   (readiness score ≠ permission; gates override outcomes)  
   → `docs/week-02/03_decision_thresholds_and_gates.md`

4. **Minimum Controls by Risk Tier**  
   (incl. Tier 3: mandatory quarterly “Red-Button” kill-switch drills)  
   → `docs/week-02/04_minimum_controls_by_risk_tier.md`

5. **Dimension Weighting Matrix**  
   → `docs/week-02/05_weighting_matrix.md`

6. **Assessment Questionnaire (Evidence Support)**  
   → `docs/week-02/06_assessment_questionnaire.md`

---

### 📁 Week 3 — Reference Architecture (Planned)

Located under `docs/week-03/` (to be added)

Planned deliverables:
- Enterprise GenAI reference architecture
- Agentic AI reference architecture
- Guardrail & monitoring middleware
- Schema contracts (inputs, outputs, evidence, logs)
- Escalation/failure patterns and kill-switch implementation patterns
- Audit log schema and retention/access patterns

---

### 📁 Week 4 — Worked Example (Completed)

Located under `docs/week-04/`

A full application of the framework to a real GenAI system (**GenAI Contract Risk Analyzer**):

1. **Worked Example Overview**  
   → `docs/week-04/01_worked_example_overview.md`

2. **Scorecard and Governance Gates**  
   (Tier 2 classification + weighted calculation + gate outcomes)  
   → `docs/week-04/02_scorecard_and_gates.md`

3. **Decision and Remediation Plan**  
   (Pilot controls + P0/P1/P2 roadmap + re-evaluation triggers)  
   → `docs/week-04/03_decision_and_remediation_plan.md`

---

## Intended Audience

This framework is intended for:

- Heads of AI / GenAI / Digital Transformation
- AI Product and Platform Owners
- Enterprise Architects
- Risk, Compliance, and Legal stakeholders
- Consulting and advisory leaders working in regulated environments

---

## Disclaimer

This repository is provided for **professional and educational demonstration purposes**.  
It does not contain proprietary methodologies, confidential client information, or internal organizational policies.

---

## Author

Created by an enterprise digital transformation leader with hands-on experience in:
- GenAI solution design
- Agentic AI systems
- AI governance and risk management
- Large-scale enterprise transformation

---

## Status

🟢 **Active development**  
✅ Week 1, Week 2, and Week 4 completed (v1)  
🟡 Week 3 Reference Architecture planned next
