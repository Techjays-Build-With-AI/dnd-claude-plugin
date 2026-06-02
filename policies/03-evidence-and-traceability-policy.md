# 03 — Evidence & Traceability Policy

**Purpose:** make scope defensible. Every requirement and assumption must be traceable to where it
came from, so disputes ("we never said that") are settled by evidence, not memory.

## Rules
1. **Every requirement and assumption has a source.** Record where it came from: interview, document,
   sample, system, email, screenshot, or client confirmation.
2. **Facts require evidence.** An item classified as a *Fact* (see
   [Policy 04](./04-classification-policy.md)) with no source artifact is **downgraded to an
   Assumption** and surfaces in the RAID Register.
3. **Confidence is recorded.** Each item carries a confidence (High / Medium / Low) and a validation
   status (Validated / Pending / Not validated).
4. **Requirements link to examples.** Per [Policy 02](./02-example-based-validation-policy.md), each
   important requirement links to one or more real client examples (example traceability).
5. **One source of truth.** Items are owned in the RAID Register and the Scope Document; other
   documents reference them rather than restating them.

## Evidence record (shape)

| Requirement / item | Source | Evidence type | Confidence | Validated by |
|--------------------|--------|---------------|-----------:|--------------|
| System extracts invoice no., vendor, date, amount, tax, line items | AP interview + sample invoices | Interview + samples | 85% | Pending |
| Invoices above $10,000 need manager approval | Finance Lead interview | Interview | 70% | Pending |
| ERP supports invoice update via API | IT call note | Verbal | 50% | Not validated |

## Why it matters
- *"Why did we include this?"* → trace to the artifact/example.
- *"Why was this not included?"* → "that scenario was not provided or validated during D&D."
- Low-confidence, unvalidated items are exactly the ones that must either be closed before estimate
  or written into the SOW as assumptions.

## Agent enforcement
- Refuses to record a Fact without a source; auto-reclassifies to Assumption and notes the gap.
- Tracks confidence and validation status on every captured item and rolls them into readiness
  scoring (low-confidence items depress the relevant dimension).
- Maintains the evidence/traceability table and can produce the "why in / why out" justification for
  any scope item on demand.
