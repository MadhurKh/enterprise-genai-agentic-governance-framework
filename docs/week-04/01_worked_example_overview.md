# Worked Example Overview — GenAI Contract Risk Analyzer

## Purpose

This worked example demonstrates how to apply the **Enterprise GenAI & Agentic AI Governance and Evaluation Framework** to a real system: **GenAI Contract Risk Analyzer**.

It converts the theoretical framework into a practical **Governance Record** that is:

- Decision-ready (Approve / Pilot / Block)
- Audit-friendly (traceable rationale and assumptions)
- Proportional (controls scale with risk tier)

---

## System Summary

- **System Name:** GenAI Contract Risk Analyzer
- **System Type:** Enterprise GenAI decision-support tool (portfolio/POC demo)
- **Business Goal (Context):** Reduce manual legal/procurement contract triage time by **~40%**, while improving consistency of risk identification across high-volume procurement contracts.
- **Primary Function:** Analyze contracts to identify high-risk clauses, provide explanations for flags, map evidence (where possible), and suggest remediation language to human reviewers.

---

## Governance Context (Locked Assumptions)

Governance decisions are context-dependent. To ensure a consistent evaluation, the following assumptions are locked for this worked example:

1. **Intended usage:** Internal legal and procurement teams only (portfolio/POC)
2. **Connectivity:** Read-only access to contract inputs; **no write-back** authority to any Contract Lifecycle Management (CLM) / Contract Management System
3. **Data type:** Synthetic or strictly anonymized contract data (no PII)
4. **Human oversight:** Mandatory human review of every flag before a contract is progressed
5. **Model sourcing:** External LLM accessed via enterprise API
6. **Fallback strategy:** Manual fallback (graceful degradation to checklist/rules + “needs review” state)

---

## Governance Classification Summary

- **Risk Tier:** **Tier 2 (Decision Support / Medium Risk)**
- **Autonomy Level:** Recommendation-only (no execution authority)
- **Required Oversight:** End-user verification; SME sampling review for material decisions (as applicable)
- **Initial Outcome:** **Pilot with Controls**
- **Next Re-evaluation:** End of a **3-month pilot** or earlier upon any material change (e.g., real data, scope expansion, vendor/model change)

---

## How to Read This Worked Example

This worked example is split into:

1. **Scorecard and Governance Gates**  
   Weighted score calculation + gate pass/fail outcomes  
   → `02_scorecard_and_gates.md`

2. **Decision and Remediation Plan**  
   Pilot controls + P0/P1/P2 remediation roadmap and triggers  
   → `03_decision_and_remediation_plan.md`

---

## Why This Example Matters

Many AI governance frameworks remain theoretical. This worked example demonstrates how the framework can:

- Justify a governance outcome with explicit assumptions
- Prove that readiness scoring is mathematically defensible
- Prevent unsafe deployment through hard permission gates
- Translate governance outcomes into an actionable engineering roadmap
