# Example-Based Validation Coverage

> **Core rule:** No workflow is considered scoped unless it has been walked through using actual
> client examples — documents, records, transactions, screenshots, emails, reports, or sample cases.

Stakeholders describe the happy path. Scope creep comes from everything they *don't* mention:
exceptions, uncommon cases, document variations, hidden approvals, manual judgment, bad data, missing
fields, system limitations, edge cases. **Real examples expose these.** So the agent asks for
examples, not just answers.

## The three required example types

Each workflow should be validated with at least three example types:

| Type | What it is | Purpose |
|------|------------|---------|
| **Happy path** | A normal case where everything works (clean invoice, vendor exists, PO matches, within tolerance). | Proves the standard workflow. |
| **Exception** | Something breaks or needs human judgment (missing PO, amount mismatch, duplicate, missing vendor, unreadable PDF, delayed approval). | Exposes hidden scope. |
| **Edge / complex** | Infrequent but business-critical (confidential invoice, netted statement, multi-line, partial payment, credit memo, split GL coding, multi-department approval, override). | Protects fixed-bid scope. |

Coverage scoring: 3/3 = 100%, 2/3 = 67%, 1/3 = 33%, 0/3 = 0%. Thresholds and the hard gate are in
[readiness-scoring.md](./readiness-scoring.md#3-the-example-coverage-gate-hard-rule).

## Workflow Example Validation record

The agent maintains one record per (workflow × example), using the template in
[`../templates/workflow-example-validation.md`](../templates/workflow-example-validation.md):

Workflow name · Client example used · Source type · Scenario type (standard/exception/edge) ·
Walkthrough completed? · Current-state steps verified? · Future-state handling defined? · Business
rules confirmed? · Exception handling confirmed? · Data fields verified? · Acceptance criteria
derived? · Client validation status (Pending / Approved / Needs Revision).

## The example run-through (per example)

For every client example, run all three checklists:

**A. What happened in the real case?**
What triggered the workflow · who received it first · what document/data was used · what system was
opened · what decision was made · who approved it · what exception occurred · final output · how long
it took · what caused delay or rework.

**B. How should the future AI-native system handle it?**
What should AI extract/classify/summarise/recommend · what should deterministic software validate ·
what stays human-approved · what is auto-routed · what is logged for audit · what happens if AI
confidence is low · what happens if required data is missing · what triggers escalation.

**C. What scope decisions came from this example?**
New requirement · new business rule · new exception · new data field · new integration need · new
out-of-scope item · new assumption · new acceptance criterion.

## Example traceability

Every important requirement traces to one or more real examples. This makes scope **defensible**:

| Requirement | Linked client example | Evidence type | Confidence |
|-------------|----------------------|---------------|-----------:|
| Detect duplicate invoices | Invoice #INV-1045 duplicate case | Sample + AP explanation | High |
| Route missing-PO invoices to AP review | Vendor ABC missing-PO case | Email thread + ERP screenshot | High |

- If asked *"why did we include this?"* → point to the example.
- If asked *"why isn't this included?"* → "that scenario was not provided or validated during D&D."

## How the agent should ask

Not: *"How does invoice approval work?"*
But: *"Please share 3 recent invoices — one normal, one that required exception handling, and one
complex case that took longer than usual. We'll walk through each step-by-step to validate the
workflow."*
