# Evaluation Questionnaire (Sample)

## Usage Guidance

This questionnaire is intended to support **consistent and defensible scoring** against the Dimension-Level Scoring Anchors.

It is not exhaustive, but provides example questions that reviewers may use to:
- Justify assigned scores
- Identify missing evidence
- Support audit and governance review

---

### Dimension 2: Risk & Compliance Exposure
- [ ] Has a Legal/Compliance officer reviewed the data inputs?
- [ ] Are there specific regulations (GDPR, EU AI Act, HIPAA) that apply?
- [ ] What is the "Maximum Theoretical Loss" if this AI provides a wrong answer?

### Dimension 4: Governance & Auditability
- [ ] Can we recreate the exact prompt and model version used for a specific decision 6 months ago?
- [ ] Is every AI output timestamped and linked to a unique User ID?
- [ ] Who is the specific human individual (name/role) responsible for this system?

### Dimension 6: Agentic Safety & Control
- [ ] Does the agent have the "authority" to delete data or spend money?
- [ ] Is there a "Circuit Breaker" that stops the agent if it enters an infinite loop?
- [ ] Can a human interject and stop the agent mid-execution?