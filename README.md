# Enterprise GenAI & Agentic AI Governance and Evaluation Framework

This repository contains a practical, enterprise-ready framework for evaluating, governing, and safely operationalizing **Generative AI (GenAI)** and **Agentic AI** systems.

It is aligned with **European enterprise governance best practices**, emphasizing **risk proportionality, accountability, auditability, sovereignty, and controlled autonomy**—not hype-driven adoption.

**Core principle:** Readiness is not permission.

---

## Executive Summary (1-page)

- Executive Summary PDF: `Executive_Summary.pdf`

---

## Why This Framework Exists

Most organizations can build a GenAI proof-of-concept. Far fewer can govern it into enterprise production.

The result is **“POC purgatory”**:
- Risk and Legal teams cannot confidently approve production use
- Engineering teams lack a clear set of non-negotiable controls
- Leaders cannot defend decisions during audits or incidents

This framework bridges the gap between innovation and enterprise risk by providing a **repeatable, defensible decision model** for GenAI and Agentic AI adoption.

---

## Scope

This framework applies to:

- Enterprise GenAI applications (internal or client-facing)
- Agentic AI systems with bounded or conditional autonomy
- AI systems influencing decisions, recommendations, or execution
- Regulated or high-impact business environments

**Out of scope by design:**
- Research-only prototypes
- Academic model benchmarking
- Open-ended consumer chatbots
- Vendor-specific or proprietary implementations

---

## Repository Structure

### Week 1 — Foundation (Completed)
Location: `docs/week-01/`

1. Scope and Positioning  
   `docs/week-01/01_scope_and_positioning.md`

2. Governance Philosophy  
   `docs/week-01/02_governance_philosophy.md`

3. AI Use-Case Risk Classification (Tier 1–3)  
   `docs/week-01/03_ai_use_case_risk_classification.md`

4. Evaluation Dimensions (incl. Vendor & Model Sovereignty)  
   `docs/week-01/04_evaluation_dimensions.md`

5. Decision & Approval Logic  
   `docs/week-01/05_decision_and_approval_logic.md`

6. Framework Structure & Table of Contents  
   `docs/week-01/06_framework_structure_and_toc.md`

---

### Week 2 — Scoring and Permission Model (Completed)
Location: `docs/week-02/`

1. Scoring Model Overview  
   `docs/week-02/01_scoring_model_overview.md`

2. Dimension Scoring Anchors  
   `docs/week-02/02_dimension_scoring_anchors.md`

3. Decision Thresholds and Hard Governance Gates  
   `docs/week-02/03_decision_thresholds_and_gates.md`

4. Minimum Controls by Risk Tier  
   `docs/week-02/04_minimum_controls_by_risk_tier.md`

5. Weighting Matrix  
   `docs/week-02/05_weighting_matrix.md`

6. Assessment Questionnaire  
   `docs/week-02/06_assessment_questionnaire.md`

---

### Week 3 — Reference Architecture (Completed)
Location: `docs/week-03/`

1. Architecture Overview  
   `docs/week-03/01_architecture_overview.md`

2. GenAI Reference Architecture (Tier 1–2 baseline)  
   `docs/week-03/02_genai_reference_architecture.md`

3. Agentic AI Reference Architecture (Tier 2–3)  
   `docs/week-03/03_agentic_ai_reference_architecture.md`

4. Guardrails and Control Plane (Policy-as-code, Circuit Breaker, Kill Switch)  
   `docs/week-03/04_guardrails_and_control_plane.md`

5. Schema Contracts (incl. Sovereignty Metadata)  
   `docs/week-03/05_schema_contracts.md`

6. Audit Logging and Evidence Store (incl. Privacy & Redaction Layer)  
   `docs/week-03/06_audit_logging_and_evidence_store.md`

---

### Week 4 — Worked Example (Completed)
Location: `docs/week-04/`

1. Worked Example Overview  
   `docs/week-04/01_worked_example_overview.md`

2. Scorecard and Gates (Tier classification + weighted score)  
   `docs/week-04/02_scorecard_and_gates.md`

3. Decision and Remediation Plan (P0/P1/P2 roadmap)  
   `docs/week-04/03_decision_and_remediation_plan.md`

---

### Week 5 — Templates Pack (Completed)
Location: `docs/week-05/`

1. Templates Pack Overview  
   `docs/week-05/01_templates_pack_overview.md`

2. Use-Case Intake Form  
   `docs/week-05/02_use_case_intake_form.md`

3. Evaluation Scorecard Template (8 dimensions + weighting + calculation)  
   `docs/week-05/03_evaluation_scorecard_template.md`

4. Hard Governance Gates Checklist (Permission)  
   `docs/week-05/04_hard_governance_gates_checklist.md`

5. Minimum Controls Checklist by Risk Tier  
   `docs/week-05/05_minimum_controls_checklist_by_tier.md`

6. Audit Evidence Packet Template  
   `docs/week-05/06_audit_evidence_packet_template.md`

7. Change Control and Re-Certification Template  
   `docs/week-05/07_change_control_and_recertification.md`

---

### Week 6 — Operating Model (Completed)
Location: `docs/week-06/`

1. Operating Model Overview  
   `docs/week-06/01_operating_model_overview.md`

2. RACI and Decision Rights  
   `docs/week-06/02_raci_and_decision_rights.md`

3. Governance Cadence and Review Cycles  
   `docs/week-06/03_governance_cadence_and_review_cycles.md`

4. Exception Management and Policy Waivers  
   `docs/week-06/04_exception_management_and_policy_waivers.md`

5. Operational Assurance Plan  
   `docs/week-06/05_operational_assurance_plan.md`

6. Governance Metrics and KPIs  
   `docs/week-06/06_governance_metrics_and_kpis.md`

---

## Intended Audience

This framework is intended for:

- Heads of AI / GenAI / Digital Transformation
- AI Product and Platform Owners
- Enterprise Architects
- Risk, Compliance, and Legal stakeholders
- Consulting and advisory leaders working in regulated environments

---

## How to Use This Framework (Recommended Workflow)

1. **Classify**  
   Assign the use case to Tier 1, 2, or 3 based on autonomy and impact.

2. **Score**  
   Evaluate against the 8 dimensions and compute the tier-weighted readiness score.

3. **Gate**  
   Apply non-negotiable hard governance gates (HITL, auditability, sovereignty, security).

4. **Decide**  
   Approve / Pilot with Controls / Block & Redesign, and assign accountable owners.

5. **Operationalize**  
   Implement mandatory controls and test them (including circuit breaker behavior and kill-switch drills for Tier 3).

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

🟢 **v1 Complete (Weeks 1–6)**  
Next: **Week 7 — Starter Kit (Filled Examples + Adoption Guide)**
