# Use-Case Intake Form (Template)

## 1) Use Case Identification

- **Use Case Name:**
- **Use Case ID (slug):**
- **Business Function:** (e.g., Legal, Finance, Procurement, Customer Ops)
- **Primary Stakeholder / Business Owner:**
- **AI Product Owner:**
- **Platform / Engineering Owner:**
- **Risk / Compliance Contact:**
- **Legal Contact (if applicable):**
- **Target Go-Live Date (Pilot / Prod):**

---

## 2) Business Context and Objective

- **Business problem being solved (1–2 lines):**
- **Current baseline process:** (manual steps, cycle time, error rate)
- **Target improvement:** (e.g., reduce review time by 40%, reduce rework by 25%)
- **Expected business impact:** (time, cost, quality, risk reduction)
- **Why now:** (e.g., POC purgatory, audit demand, EU AI Act readiness)

---

## 3) User and Decision Context

- **Primary users:** (roles, teams)
- **Decision impact:** Does this influence material decisions? (Yes/No)
- **Decision criticality:** (Low / Medium / High)
- **Who is accountable for outcomes:** (name/role)
- **Who verifies outputs:** (end-user / SME / auditor)

---

## 4) Risk Tier Classification (Proposed)

- **Proposed tier:** Tier 1 / Tier 2 / Tier 3
- **Why this tier:** (autonomy posture + impact)
- **Does the system execute actions?** (Yes/No)
- If yes: **what actions** and **what limits**?

---

## 5) Data and Security

- **Data classes involved:** Public / Internal / Confidential / PII / PHI / PCI
- **Data sources:** (systems, repositories, document types)
- **Data residency requirement:** EU-only / global / on-prem
- **Security constraints:** (encryption, access rules, DLP, logging constraints)
- **Retention requirement:** (duration + policy)

---

## 6) Model and Vendor Context (Sovereignty)

- **Model provider(s):** (planned)
- **Model(s) / versions:** (planned)
- **Internal Model Gateway used?** Yes/No  
  - If no: explain why and remediation plan
- **Fallback strategy:** (secondary model, manual mode, provider outage plan)

---

## 7) Tooling and Integrations (Agentic / Tool Use)

- **Tools used:** (read tools / write tools)
- **Write authority present?** Yes/No
- **Tool permission model:** (RBAC, scopes, tier-based)
- **Rollback strategy for write actions:** (required for Tier 3)

---

## 8) Governance and Controls (Initial Plan)

- **HITL checkpoints:** (where and who)
- **Audit logging:** (events captured, evidence stored)
- **Circuit breaker / kill switch:** (auto-trip conditions + manual switch)
- **Monitoring plan:** (quality, drift, incidents)
- **Review cadence:** (Tier-based)

---

## 9) Outputs and Evidence

- **Output format:** Free text / JSON schema / hybrid
- **Schema contracts defined?** Yes/No
- **Evidence approach:** citations / snippet hashes / references
- **Explainability expectations:** (what must be explainable and to whom)

---

## 10) Approval Request

- **Requesting outcome:** Approve / Pilot with Controls / Block & Redesign
- **Scope of pilot:** (users, duration, data limits, blast radius)
- **Known gaps (P0/P1/P2):** (list)
- **Sign-off required (per tier):** (list roles)

---

## Appendix: Attachments

- Architecture diagram (Week 3)
- Scorecard draft (Week 2 template)
- Gate checklist (Week 2/5)
- Evidence packet plan (Week 3/5)
