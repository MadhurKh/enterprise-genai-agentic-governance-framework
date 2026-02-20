# Enterprise GenAI & Agentic AI Governance and Evaluation Framework

This repository contains a practical, enterprise-ready framework for evaluating, governing, and safely operationalizing **Generative AI (GenAI)** and **Agentic AI** systems.

It is aligned with **European enterprise governance best practices**, emphasizing **risk proportionality, accountability, auditability, sovereignty, and controlled autonomy**—not hype-driven adoption.

**Core principle:** Readiness is not permission.

---

## Executive Summary (2-pages)

- Executive Summary PDF: `Executive_Summary_v2.pdf`

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

### 📁 Week 1 — Foundation (Completed)

Located under `docs/week-01/`

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

### 📁 Week 2 — Scoring and Permission Model (Completed)

Located under `docs/week-02/`

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

### 📁 Week 3 — Reference Architecture (Completed)

Located under `docs/week-03/`

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

### 📁 Week 4 — Worked Example (Completed)

Located under `docs/week-04/`

1. Worked Example Overview  
   `docs/week-04/01_worked_example_overview.md`

2. Scorecard and Gates (Tier classification + weighted score)  
   `docs/week-04/02_scorecard_and_gates.md`

3. Decision and Remediation Plan (P0/P1/P2 roadmap)  
   `docs/week-04/03_decision_and_remediation_plan.md`

---

### 📁 Week 5 — Templates Pack (Completed)

Located under `docs/week-05/`

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

### 📁 Week 6 — Operating Model (Completed)

Located under `docs/week-06/`

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

### 📁 Week 7 — Starter Kit (Completed)

Located under `docs/week-07/`

1. Adoption Guide (30/60/90 day rollout + Tier 1 fast-track)
   `docs/week-07/01_adoption_guide.md`

2. Filled Use-Case Intake Example (Contract Risk Analyzer)
   `docs/week-07/02_filled_use_case_intake_example.md`

3. Filled Scorecard Example (evidence maturity + weighted math)
   `docs/week-07/03_filled_scorecard_example.md`

4. Filled Hard Governance Gates Checklist Example (Pass with conditions)
   `docs/week-07/04_filled_gates_checklist_example.md`

5. Policy Exception Register Example
   `docs/week-07/05_exception_register_example.md`

6. Re-Certification Example (Context Drift)
   `docs/week-07/06_recertification_example_context_drift.md`

---

### 📁 Week 8 — Enforcement Patterns (Policy, Gateway, Circuit Breaker) (Completed)

Located under `docs/week-08/`

1. **Policy-as-Code Blueprint**  
   Defines pre-flight / in-flight / post-flight policy checks, policy input contract, and enforcement approach  
   → `01_policy_as_code_blueprint.md`

2. **Internal Model Gateway Pattern**  
   Enterprise vendor abstraction for sovereignty routing, metadata capture, and fallback behavior  
   → `02_internal_model_gateway_pattern.md`

3. **Circuit Breaker and Safe Fallback**  
   Auto-trip circuit breaker vs manual kill switch, degrade modes, trigger thresholds (safety + cost)  
   → `03_circuit_breaker_and_safe_fallback.md`

4. **Reference Implementation Checklist**  
   Tier-wise “Definition of Done” for governance + enforcement capabilities  
   → `04_reference_implementation_checklist.md`

5. **Validation Test Plan**  
   Test cases covering policy enforcement, sovereignty, redaction, replay, and jailbreak attempts  
   → `05_validation_test_plan.md`

---

### 📁 Week 9 — Executive + Audit Pack (Completed)

Located under `docs/week-09/`

1. **Executive Operating Standard (One-Pager)**  
   Board-ready summary: tiering, readiness vs permission, fast-track for Tier 1, mandatory evidence  
   → `01_executive_operating_standard_one_pager.md`

2. **AI Governance Board Pack (Outline)**  
   Slide outline for governance boards including runtime risk signals, drift, and ROI realization  
   → `02_ai_governance_board_pack_outline.md`

3. **Controls Crosswalk (EU Enterprise Assurance)**  
   Maps EU governance themes to framework controls and evidence artifacts  
   → `03_controls_crosswalk_eu_enterprise_assurance.md`

4. **Audit-Ready Evidence Index**  
   Checklist to assemble audit packets (incl. jailbreak test results and privacy/redaction evidence)  
   → `04_audit_ready_evidence_index.md`

5. **Adoption in 2 Weeks (Quickstart)**  
   Minimum Viable Governance rollout plan with Day 0 executive sponsorship  
   → `05_adoption_in_2_weeks_quickstart.md`

---

### 📁 Week 10 — Reference Implementation Starter Kit (Completed)

Located under `docs/week-10/`

1. **Reference Implementation Kit Overview**  
   How Week 10 artifacts map to enforcement, operations, and audit requirements  
   → `01_reference_implementation_kit_overview.md`

2. **Policy-as-Code (Rego Samples)**  
   Practical enforcement rules including Tier 2/3 fail-closed posture  
   → `01_policy_as_code_rego_samples.md`

3. **Model Gateway OpenAPI Contract**  
   Vendor abstraction contract including 429 throttling and Retry-After expectations  
   → `02_model_gateway_openapi_contract.yaml`

4. **Gateway Routing Table Example**  
   Routing logic including 429/quota fallback patterns and governance logging guidance  
   → `03_model_gateway_routing_table_example.md`

5. **Circuit Breaker Runbook**  
   Auto-trip + manual kill switch operational procedure (includes cost breach triggers)  
   → `04_circuit_breaker_runbook.md`

6. **Alerts and SLO Examples**  
   Monitoring expectations aligned to governance KPIs and incident thresholds  
   → `05_alerts_and_slos_examples.md`

7. **Audit Event Schema Examples (JSONL)**  
   Replayable, privacy-first logging examples including `redaction_summary` and `correlation_id` chaining  
   → `06_audit_event_schema_examples.jsonl`

8. **Tiered Release Readiness Checklist**  
   Production readiness criteria by tier (Tier 3 includes threat model / pen-test expectation)  
   → `07_release_readiness_checklist_tiered.md`

---

### 📁 Week 11 — Implementation Packaging + “MVI” Walkthroughs (Completed)

Located under `docs/week-11/`

1. **Implementation Packaging Guide (Where Artifacts Live)**  
   Standard folder structure, System of Record guidance, and cross-referencing rules  
   → `01_implementation_packaging_guide.md`

2. **Minimum Viable Implementation Walkthrough (Tier 2)**  
   End-to-end steps from intake → permission → pilot → ops → audit packet  
   → `02_mvi_walkthrough_tier2.md`

3. **Minimum Viable Implementation Walkthrough (Tier 3)**  
   End-to-end enforcement flow including policy-as-code, fail-closed, breaker + quarterly drills  
   → `03_mvi_walkthrough_tier3.md`

4. **Engineering Repo Starter Templates**  
   - Policy change governance template → `04_POLICY_template.md`  
   - Evidence capture guide template → `05_EVIDENCE_template.md`  
   - Incident response runbook template → `06_RUNBOOK_template.md`

5. **Executive Visuals Blueprint (Carousel Outline)**  
   Ready structure for a LinkedIn / internal comms PDF carousel summarizing the framework  
   → `07_executive_visuals_blueprint.md`

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

🟢 **v1 Complete (Weeks 1–7)**  
Next: **Week 8 — Implementation Blueprint (Policy-as-Code + Model Gateway + Circuit Breaker patterns)**
