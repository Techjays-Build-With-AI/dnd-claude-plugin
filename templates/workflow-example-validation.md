# Workflow Example Validation — <MODULE / WORKFLOW>

> One record per (workflow × example). A workflow is not scope-ready until it has a validated
> happy-path, exception, and edge/complex example (see Policy 02).

## Example record

| Field | Details |
|-------|---------|
| Workflow name | |
| Client example used | (e.g. Invoice #INV-1045 from Vendor ABC) |
| Source type | (PDF + ERP screenshot + email thread …) |
| Scenario type | Standard / Exception / Edge |
| Walkthrough completed? | Yes / No |
| Current-state steps verified? | Yes / No |
| Future-state handling defined? | Yes / No |
| Business rules confirmed? | Yes / No |
| Exception handling confirmed? | Yes / No |
| Data fields verified? | Yes / No |
| Acceptance criteria derived? | Yes / No |
| Client validation status | Pending / Approved / Needs Revision |

## A. What happened in the real case?
Trigger · who received it first · document/data used · system opened · decision made · who approved ·
exception that occurred · final output · how long it took · cause of delay/rework.

## B. How should the AI-native system handle it?
What AI extracts/classifies/recommends · what deterministic software validates · what stays
human-approved · what is auto-routed · what is logged · low-confidence handling · missing-data
handling · escalation trigger.

## C. Scope decisions from this example
New requirement · new business rule · new exception · new data field · new integration need · new
out-of-scope item · new assumption · new acceptance criterion.

## Coverage summary for this workflow
| Example type | Provided? | Validated? |
|--------------|:---------:|:----------:|
| Happy path | | |
| Exception | | |
| Edge / complex | | |

**Coverage %:** __ · **Decision:** (100% ready · 67% estimate-with-assumptions · 33% not ready · 0% exclude/future)
