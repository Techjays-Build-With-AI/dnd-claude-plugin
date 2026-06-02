# Classification Taxonomy

Every captured item must be classified as exactly one of the types below. Classification is what
turns discovery from note-taking into **scope governance** — it forces each statement to declare its
epistemic status (do we *know* this, or do we *believe* it?) and routes it to the right home in the
[RAID Register](./dnd-schema.md#document-4--raid-register-the-conditions-the-price-depends-on).

## The six types

| Type | Meaning | Lives in |
|------|---------|----------|
| **Fact** | Confirmed from artifact, system, or stakeholder. | Scope / Architecture (with evidence link) |
| **Assumption** | Believed to be true but not confirmed. Estimate depends on it. | RAID → Assumptions |
| **Decision** | Explicitly agreed by client/Techjays. | Decision log (Validation pack) |
| **Open Question** | Needs clarification before we can rely on it. | RAID → Open Questions |
| **Risk** | May impact scope, timeline, or cost. | RAID → Risks |
| **Dependency** | Requires client/system/vendor action. | RAID → Dependencies |

### Worked examples
- *Fact:* "Invoices are received through a shared AP inbox." (confirmed in AP interview + screenshot)
- *Assumption:* "Most invoice PDFs follow a standard structure." (believed, not yet validated)
- *Open Question:* "Does the ERP provide an API for invoice creation?"
- *Decision:* "Payment execution is out of scope for Phase 1."
- *Risk:* "If the ERP API is unavailable, integration timeline may increase."
- *Dependency:* "Client must provide a sandbox ERP environment by <date>."

## Open-question sub-classification (gating)

Every **Open Question** also gets exactly one sub-class. This determines whether a module can be
estimated:

| Sub-class | Effect on scope |
|-----------|-----------------|
| **Must close before estimate** | Blocks fixed-bid for the affected module until resolved. |
| **Proceed with assumption** | Convert to an Assumption (write into SOW) and continue. |
| **Minor implementation detail** | Does not block; resolved during build. |
| **Too uncertain (exclude / T&M)** | Remove from fixed bid; recommend T&M or future phase. |
| **Future phase** | Explicitly deferred; recorded in Implementation Plan phasing. |

## Rules for the agent
1. **No unclassified items.** Anything captured during discovery carries a type before it can affect
   readiness scoring.
2. **Facts require evidence.** A "Fact" with no source artifact is downgraded to an Assumption — see
   the [Evidence & Traceability Policy](../policies/03-evidence-and-traceability-policy.md).
3. **Assumptions surface in the SOW.** A "Ready with Assumptions" verdict must list every assumption
   the estimate relies on.
4. **Don't duplicate.** Items are owned in the RAID Register; other documents point to it.
