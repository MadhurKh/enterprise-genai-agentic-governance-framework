# Week 6 — Operating Model (How Enterprises Run This Framework)

## Purpose

Week 6 defines the **operating model** required to run the governance framework at scale:
- clear ownership (RACI)
- defined governance bodies and decision rights
- cadence and artefacts for reviews
- assurance mechanisms (tests, evidence, sampling)
- metrics that show whether governance is working (and not blocking value)

This turns the framework from a “playbook” into a **repeatable enterprise process**.

---

## Core Principle

**Readiness is not permission.**  
Readiness is determined by scoring; permission is determined by governance gates and accountable sign-off.

---

## Governance Bodies (Recommended)

### 1) AI Use-Case Review Board (UCRB)
**Purpose:** intake, tier confirmation, score review, pilot approval conditions  
**Typical members:** AI Product Owner, Business Owner, Platform Owner, Risk/Compliance, Legal (Tier 2/3), Domain SME

### 2) AI Risk & Controls Council (ARCC)
**Purpose:** gate interpretation, exception approvals, control uplift decisions  
**Typical members:** Risk, Legal, Security, Internal Audit rep, AI Platform Owner

### 3) Tier 3 Executive Approval Forum
**Purpose:** approve/deny Tier 3 deployments, validate kill-switch readiness, auditor plan  
**Typical members:** Executive Business Owner, Risk, Legal, AI Platform Owner, Independent AI Auditor

---

## Standard Workflow (Run State)

1. **Intake** (Week 5 form)  
2. **Tier Confirmation** (Week 1)  
3. **Scorecard** (Week 5, backed by Week 2 anchors + weights)  
4. **Hard Gates** (Week 5 gate checklist)  
5. **Pilot Decision + Controls** (Week 5 controls checklist)  
6. **Evidence Packet Assembly** (Week 5 evidence pack)  
7. **Go/No-Go** (Board decision + sign-offs)  
8. **Operate & Monitor** (Week 3 ops layer + Week 6 cadence)  
9. **Re-certification** (Week 5 change control triggers)

---

## Outputs (Operational Artifacts)

- Intake form (per use case)
- Tier classification record
- Scorecard with evidence maturity levels
- Gate checklist (pass/fail) + remediation items
- Controls checklist + implementation proof
- Audit evidence packet
- Exception register (if applicable)
- Re-certification record (change control)

---

## Governance Health KPIs (Performance-Managed)

These KPIs measure whether governance is actually operating (not just documented).

1. **Tier 3 Kill-Switch Drill Compliance (% current)**  
   % of Tier 3 systems with a **successful kill-switch drill within the last 90 days** (evidence captured).

2. **Time-to-Remediate Block Conditions (Median days)**  
   Median time from a **Block / Redesign** decision to closure of P0 remediation items and re-evaluation.

3. **HITL Override Ratio (Overrides / Total decisions)**  
   Ratio of HITL overrides vs approvals, tracked by tier and by use case.  
   Spikes indicate quality drift, retrieval failure, poor SOP training, or unsafe autonomy boundaries.

4. **Gate Pass Rate (First Review)**  
   % of use cases passing hard governance gates on the first review (Tier 2/3).  
   Low rates signal upstream architecture/control weaknesses or unclear design standards.

---

## When This Operating Model Is Mandatory

- **Tier 1:** recommended (lightweight)
- **Tier 2:** mandatory for production and any regulated pilot
- **Tier 3:** mandatory for any environment beyond isolated development
