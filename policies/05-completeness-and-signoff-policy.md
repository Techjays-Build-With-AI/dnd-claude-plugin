# 05 — Completeness & Sign-off Policy

**Purpose:** define when discovery is "mature enough," what the agent produces along the way, and how
scope is frozen.

## Maturity before generation
Do **not** generate a large final document early. Build the structured project knowledge model first
(see [`../templates/project-knowledge-model.md`](../templates/project-knowledge-model.md)); generate
documents from it only once the relevant sections reach maturity.

A **module** is "mature / scope-ready" only when:
- its required schema sections are filled (see [`../reference/dnd-schema.yaml`](../reference/dnd-schema.yaml));
- example coverage is 100% and the client has validated the interpretation
  ([Policy 02](./02-example-based-validation-policy.md));
- its items are classified ([Policy 04](./04-classification-policy.md)) with no open
  *Must-close-before-estimate* questions;
- requirements trace to evidence ([Policy 03](./03-evidence-and-traceability-policy.md)).

## The three outputs

| Output | Audience | When | Contents |
|--------|----------|------|----------|
| **Discovery Health Dashboard** | Techjays delivery leadership | Continuously, every pass | Project readiness score, module-wise completeness, missing info, open questions, high-risk assumptions, unvalidated dependencies, stakeholders pending, items blocking fixed-bid estimation. Template: [`../templates/discovery-health-dashboard.md`](../templates/discovery-health-dashboard.md). |
| **Client Validation Pack** | Client | When sections mature enough to confirm | Current-state understanding, future-state recommendation, in/out of scope, assumptions, dependencies, open decisions, questions requiring confirmation. Template: [`../templates/client-validation-pack.md`](../templates/client-validation-pack.md). |
| **Final D&D Pack** | Proposal / SOW | Only after validation is sufficiently complete | The full 6-document pack per the mold: Executive Summary, Scope Document, Technical Architecture, RAID Register, Implementation Plan, Approval Page. |

## Sign-off / scope freeze (two gates)
1. **Internal PSRC gate.** The Project Solution Review Committee reviews scope & solution against the
   seven lenses (Solution Fit, Scope Completeness, Architecture Soundness, Risk & Feasibility, Effort
   & Timeline, Value & ROI, Client Impact). PSRC approval is the internal *Approve to Proceed →
   Execution Starts* gate.
2. **Client scope-freeze gate.** The client signs the Approval Page: scope-freeze statement, what is
   being approved, exclusions acknowledgement, change-control note, signatory table. This authorises
   the fixed-bid proposal.

## The freeze produces
Final scope · out of scope · assumptions · dependencies · risks · acceptance criteria · approval page.
After freeze, all change runs through change control ([Policy 01](./01-scope-control-policy.md)).

## Agent enforcement
- Maintains the Discovery Health Dashboard live; never reports a module mature unless all maturity
  conditions hold.
- Withholds the Final D&D Pack until validation is sufficiently complete; before that, produces the
  knowledge model and the validation pack.
- Produces the readiness verdict against the PSRC lenses and lists exactly what must be true (or
  written into the SOW) to freeze.
