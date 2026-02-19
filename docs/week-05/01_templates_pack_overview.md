# Week 5 — Templates Pack (Operational Artifacts)

## Purpose

Week 5 provides **copy-paste-ready templates** that turn this framework into an operating mechanism across Business, Engineering, Risk, Legal, and Platform teams.

These templates are designed to:
- reduce governance ambiguity
- standardize evidence capture
- accelerate approvals (without weakening controls)
- improve audit readiness and replayability

**Principle:** Readiness is not permission. Templates separate scoring readiness from hard permission gates.

---

## What’s Included

1. **Use-Case Intake Form**  
   `02_use_case_intake_form.md`

2. **Evaluation Scorecard (8 dimensions + weighting + calculation)**  
   `03_evaluation_scorecard_template.md`

3. **Hard Governance Gates Checklist (permission)**  
   `04_hard_governance_gates_checklist.md`

4. **Minimum Controls Checklist by Risk Tier**  
   `05_minimum_controls_checklist_by_tier.md`

5. **Audit Evidence Packet Template (what to capture, where, and how)**  
   `06_audit_evidence_packet_template.md`

6. **Change Control and Re-Certification Template**  
   `07_change_control_and_recertification.md`

---

## Recommended Workflow (End-to-End)

1. **Intake**  
   Complete the intake form for the use case and proposed deployment context.

2. **Classify (Tier 1–3)**  
   Confirm tier classification using Week 1: Risk Classification.

3. **Score (Readiness)**  
   Use the scorecard template with Week 2 anchors and weighting matrix.

4. **Gate (Permission)**  
   Apply hard governance gates checklist. If any gate fails: **Block / Redesign**.

5. **Controls (Operationalize)**  
   Use controls checklist by tier to implement required technical and process controls.

6. **Evidence (Audit-ready)**  
   Use the audit packet template to capture proof of compliance.

7. **Change control**  
   Use recertification template whenever model/prompt/tool/policy changes occur.

---

## Roles & Responsibilities (RACI by Template)

**R = Responsible (does the work)**  
**A = Accountable (final owner / sign-off)**  
**C = Consulted (must be involved)**  
**I = Informed (kept in loop)**

| Template | Business Owner | AI Product Owner | Eng / Platform Owner | Risk / Compliance | Legal | Domain SME | Independent AI Auditor |
|---|---|---|---|---|---|---|---|
| 02 Use-Case Intake Form | A | R | C | C | C (Tier 2/3) | C | I |
| 03 Evaluation Scorecard | A | R | C | C | C (Tier 2/3) | C | C (Tier 3) |
| 04 Hard Governance Gates | A | R | R | A (risk gates) | A (legal gates) | C | C (Tier 3) |
| 05 Minimum Controls Checklist | I | A | R | C | C | C | C (Tier 3) |
| 06 Audit Evidence Packet | A | R | R | C | C | C | A (Tier 3) |
| 07 Change Control & Re-Certification | A | R | R | C | C | C | C (Tier 3) |

**Note:** Tier 3 requires explicit involvement of Risk, Legal, and Independent AI Auditor as defined in Week 1/2.

---

## Audience

These templates are intended for:
- AI Product Owners and Program Leaders
- Enterprise Architects and Platform Owners
- Risk, Compliance, Legal, and Internal Audit
- Engineering leads operationalizing GenAI and agentic systems
