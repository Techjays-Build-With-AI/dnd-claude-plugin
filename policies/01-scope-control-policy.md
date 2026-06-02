# 01 — Scope Control Policy

**Purpose:** prevent scope creep by binding the committed scope to what was actually reviewed and
validated during Design & Discovery.

## Policy statement (use verbatim in SOWs and the Scope Document)

> **All workflows and features will be validated using client-provided real-world examples. Scope
> will be based on the scenarios reviewed and approved during Design & Discovery. Scenarios, document
> types, business rules, or exception cases not provided or validated during this phase will be
> treated as out of scope unless explicitly added through change control.**

## Change-control note (verbatim — from the Approval Page)

This wording is fixed. The agent and the SOW must use it identically:

> **Any new requirement, workflow, integration, report, rule, exception, data variation, third-party
> limitation, or changed assumption after approval may affect cost, timeline, and approach, and is
> handled via change control.**

## Rules

1. **Reviewed ⇒ in scope candidate; not reviewed ⇒ out of scope.** A capability becomes a candidate
   for the fixed bid only after its workflow has been validated per
   [Policy 02](./02-example-based-validation-policy.md). Silence is not inclusion.
2. **Explicit exclusions.** The Scope Document records per-module out-of-scope items and a global
   out-of-scope section; the Approval Page carries an **exclusions acknowledgement** so nothing is
   assumed included by silence.
3. **Defer, don't stretch.** When a scenario is uncertain or unvalidated, classify it (Policy 04) as
   *Future phase*, *Too uncertain (T&M)*, or *Proceed with assumption* — never silently fold it in.
4. **The baseline is the frozen pack.** The scope-freeze statement on the Approval Page defines the
   baseline: documented modules, workflows, assumptions, integrations, business rules, exceptions,
   exclusions, and acceptance criteria. Changes after freeze run through change control.
5. **Traceable inclusion/exclusion.** For any scope decision, the agent can answer *"why included?"*
   (point to the example/evidence) and *"why excluded?"* ("not provided or validated during D&D").

## Agent enforcement
- Refuses to mark a module "Ready for fixed-bid" when example coverage or client validation is below
  the gate (see [readiness-scoring.md](../reference/readiness-scoring.md)).
- Flags any requirement asserted without a linked example or evidence source.
- Surfaces every unvalidated scenario as an explicit out-of-scope / future-phase candidate rather than
  including it.
