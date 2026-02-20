# Filled Example — Use-Case Intake Form (GenAI Contract Risk Analyzer)

## 1) Use Case Identification

- **Use Case Name:** GenAI Contract Risk Analyzer
- **Use Case ID (slug):** genai-contract-risk-analyzer
- **Business Function:** Legal / Contract Management
- **Primary Stakeholder / Business Owner:** Head of Legal Operations (Example)
- **AI Product Owner:** AI Product Owner — GenAI Governance Portfolio (Example)
- **Platform / Engineering Owner:** Platform Engineering Lead (Example)
- **Risk / Compliance Contact:** Enterprise Risk Partner (Example)
- **Legal Contact (if applicable):** Legal Counsel — Contracts (Example)
- **Target Go-Live Date (Pilot / Prod):** Pilot: 4 weeks; Prod: TBD after remediation

---

## 2) Business Context and Objective

- **Business problem being solved (1–2 lines):**  
  Reduce manual legal review effort by surfacing contract risks, obligations, and missing clauses consistently.

- **Alternative non-AI baseline:**  
  Rules-based clause library + keyword search + standardized checklists + paralegal triage.

- **Current baseline process:**  
  Manual review by legal analysts; inconsistent coverage across reviewers; high cycle time during peak workloads.

- **Target improvement:**  
  Reduce first-pass review time by ~40%; improve consistency and completeness of risk identification.

- **Expected business impact:**  
  Faster contract turnaround, reduced rework, stronger compliance posture, improved audit readiness for contractual decisions.

- **Why now:**  
  Teams are stuck in “POC purgatory” due to unclear risk posture. A governed Tier 2 pilot enables controlled adoption.

---

## 3) User and Decision Context

- **Primary users:** Legal analysts, contract managers
- **Decision impact:** Yes (influences contract interpretation and negotiation priorities)
- **Decision criticality:** Medium to High (depending on contract type and value)
- **Who is accountable for outcomes:** Business Owner (Head of Legal Ops)
- **Who verifies outputs:** End-user verification + SME sampling review

---

## 4) Risk Tier Classification (Proposed)

- **Proposed tier:** Tier 2 (Decision Support)
- **Why this tier:**  
  The system provides risk identification and recommendations but does not execute contract edits or approvals autonomously.
- **Does the system execute actions?** No
- **If yes (N/A):** —

---

## 5) Data and Security

- **Data classes involved:** Confidential; may contain PII depending on contract
- **Data sources:** Uploaded contracts (PDF/DOCX); clause library; policy guidance
- **Data residency requirement:** EU-only for EU clients; otherwise enterprise standard
- **Security constraints:** RBAC; encryption in transit/at rest; DLP where required; restricted evidence storage
- **Retention requirement:** Pilot evidence retained for defined period; subject to privacy/redaction policy

---

## 6) Model and Vendor Context (Sovereignty)

- **Model provider(s):** Enterprise-approved LLM provider via internal model gateway
- **Model(s) / versions:** To be recorded per request via sovereignty metadata
- **Internal Model Gateway used?** Yes
- **Fallback strategy:**  
  Manual review mode (non-AI baseline) and alternative model routing in case of provider outage (where available).

---

## 7) Tooling and Integrations (Agentic / Tool Use)

- **Tools used:** Retrieval (RAG) over clause library and contract text; no write tools
- **Write authority present?** No
- **Tool permission model:** Read-only; RBAC on document access
- **Rollback strategy for write actions:** N/A (no write actions)

---

## 8) Governance and Controls (Initial Plan)

- **HITL checkpoints:**  
  End-user must confirm/accept findings before acting; system provides evidence/citations.
- **Audit logging:**  
  Capture request metadata, document references, prompt template version, model id/version/region, output hashes, and user actions (accept/override).
- **Circuit breaker / kill switch:**  
  Circuit breaker triggers on repeated policy/evidence failures; manual safe fallback is “manual review mode.”
- **Monitoring plan:**  
  Quality sampling, override rate monitoring, latency/cost monitoring.
- **Review cadence:**  
  Weekly during pilot; monthly post-pilot.

---

## 9) Outputs and Evidence

- **Output format:** Hybrid (structured JSON + human-readable summary)
- **Schema contracts defined?** Yes (Week 3 schema contracts)
- **Evidence approach:** Citations/snippet hashes + document references
- **Explainability expectations:**  
  Every flagged risk must include evidence references and confidence limitations.

---

## 10) Approval Request

- **Requesting outcome:** Pilot with Controls
- **Scope of pilot:**  
  Limited user group; synthetic or low-sensitivity contracts first; expand to regulated clients only after sovereignty validation.
- **Known gaps (P0/P1/P2):**  
  P0: evidence capture completeness; P1: improved fallback automation; P2: expanded sampling automation.
- **Sign-off required (per tier):**  
  BO, AIPO, RISK, LEGAL (context-dependent), SME.

---

## Appendix: Attachments

- Week 3 reference architecture diagram link
- Scorecard (filled) link
- Gates checklist (filled) link
- Evidence packet plan link
