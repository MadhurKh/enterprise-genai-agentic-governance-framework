# Week 11 — Implementation Packaging Guide (Where Artifacts Live)

**Repository:** https://github.com/MadhurKh/enterprise-genai-agentic-governance-framework  
**Generated:** 20 Feb 2026  
**Purpose:** Provide a standard folder structure and “system-of-record” mapping so the framework can be adopted without becoming scattered documents.

---

## Why This Exists

Enterprise governance fails when artifacts are distributed across emails, personal drives, and ad-hoc spreadsheets.

This guide defines:

- **Where each artifact belongs**
- **Which system is the system of record (SoR)**
- **How to link evidence across weeks**
- **How to keep audits simple and defensible**

---

## Recommended Folder Structure (Repository)

This framework repo uses `docs/week-XX/` for the official reference artifacts.

For implementation in an enterprise program, adopt a **two-repo pattern**:

1. **Framework Repo (This repo):** standards and templates (immutable reference)
2. **Use-Case Evidence Repo (per org or per portfolio):** execution artifacts and evidence (access-controlled)

---

## Recommended Use-Case Evidence Repository Layout

```
ai-governance-evidence/
  use-cases/
    UCR-CR-001_contract-risk-analyzer/
      00_intake/
        intake_form.md
        assumptions.md
      01_classification/
        tier_classification.md
      02_scorecard/
        evaluation_scorecard.md
        weighting_snapshot.md
      03_gates/
        hard_gates_checklist.md
        training_records/
      04_architecture/
        architecture_diagram.png
        schemas/
          model_input.schema.json
          model_output.schema.json
      05_validation/
        test_plan.md
        results/
          jailbreak_tests.md
          sovereignty_tests.md
          privacy_redaction_tests.md
      06_runtime_ops/
        runbooks/
        alerts_slos.md
        breaker_drill_records/
      07_audit_packet/
        audit_evidence_packet.md
        evidence_index.md
      08_exceptions/
        exception_register.md
      09_change_control/
        change_log.md
        recertification_records/
```

---

## “Drop-in” Starter Files (Engineering Repos)

To keep adoption consistent across teams, add these starter files to every Tier 2/3 implementation repo:

- `POLICY.md` → how policy rules are changed, approved, tested, and deployed
- `EVIDENCE.md` → how evidence is captured, linked, and stored (privacy-first)
- `RUNBOOK.md` → incident response aligned to breakers, kill switches, and governance

(Templates are provided in Week 11: `04_POLICY_template.md`, `05_EVIDENCE_template.md`, `06_RUNBOOK_template.md`.)

---

## System of Record (SoR) Guidance

| Artifact | Primary SoR | Notes |
|---|---|---|
| Use-case intake | GRC / Jira SecOps | Store the approval ID; link to evidence repo folder |
| Tier classification | GRC / Jira SecOps | Must be immutable per release |
| Scorecard + weighting snapshot | Evidence repo + GRC link | Scorecard can evolve; keep snapshots per release |
| Hard gates checklist | GRC / Jira SecOps | Permission is decision; store pass/conditions/owners |
| Exceptions | GRC / Jira SecOps | Must include expiry; compensating controls |
| Policies (OPA bundles) | Policy repo / Git | Version-controlled; changes trigger recert |
| Model/Prompt Version History | Model registry (e.g., MLflow) / Git | Prompt template versions + model versions; link exact versions to each release decision record for replayability |
| Gateway contract | API repo | OpenAPI in source control; link version in audit |
| Audit event schemas | Platform repo | Must be controlled and versioned |
| Validation results | Evidence repo | Include jailbreak, sovereignty, privacy, replay |
| Runbooks + drills | Ops repo + evidence snapshot | Drills must be evidenced (Tier 3 quarterly) |
| Release decision record | GRC / Jira SecOps | Final “permission” record with approvers |

---

## Cross-Referencing (How to Link Evidence)

Use stable identifiers:

- **Use Case ID:** `UCR-...`
- **Release ID:** `REL-YYYYQ#-...`
- **Policy Decision ID:** `pol-...`
- **Correlation ID:** `corr-...` (end-to-end chain across model/tool events)

Minimum cross-links in the SoR record:

- Evidence repo path
- Release ID + scorecard snapshot ID
- Gates checklist ID
- Exception IDs (if any)
- Validation report IDs
- Drill record IDs (Tier 3)

---

## Audit-Defensible Minimum

For Tier 2/3, every release must have:

- A Tier classification record (Week 1)
- Completed scorecard + weights snapshot (Week 2/5)
- Gates checklist with signatures (Week 2/5)
- Architecture + schema contracts (Week 3/8/10)
- Validation report including jailbreak attempt tests (Week 8/10)
- Runtime ops readiness: alerts + runbook (Week 6/10)
- Audit packet and evidence index (Week 5/9)
