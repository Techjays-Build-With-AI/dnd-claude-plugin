# 02 — Example-Based Validation Policy

**Purpose:** ensure scope is built on what really happens, not on described intentions. This is the
single most important anti-scope-creep control.

## Core rule (hard gate)

> **No workflow is considered scoped unless it has been walked through using actual client examples —
> documents, records, transactions, screenshots, emails, reports, or sample cases.**

A workflow may **not** be reported "Ready for fixed-bid" unless:
- it has **100% example coverage** (a happy-path, an exception, and an edge/complex example), **and**
- the client has **validated** Techjays' interpretation of each.

See coverage scoring and thresholds in
[`../reference/example-coverage.md`](../reference/example-coverage.md).

## Minimum coverage per workflow

| Type | Why it is required |
|------|--------------------|
| Happy path | Proves the standard workflow. |
| Exception | Exposes hidden scope (the usual source of creep). |
| Edge / complex | Protects the fixed bid against rare-but-critical cases. |

## Required practice
1. **Ask for examples, not just answers.** Request specific recent cases ("one normal, one that
   needed exception handling, one that took longer than usual"), then walk through each step-by-step.
2. **Run the three checklists** for every example: what really happened · how the AI-native system
   should handle it · what scope decisions came from it (see the reference file).
3. **Record a validation entry** per (workflow × example) using
   [`../templates/workflow-example-validation.md`](../templates/workflow-example-validation.md).
4. **Derive, don't assume, acceptance criteria.** Acceptance criteria for a module come out of its
   validated examples.
5. **Name what's missing.** When an example type has not been provided, state it explicitly and
   convert the gap into a next action (request specific samples) — never quietly assume the case.

## Agent enforcement
- Treats every workflow as having an Example-Based Validation section that must reach 100% coverage.
- Computes an example-coverage score per module and blocks the readiness gate below it.
- For each missing example type, emits a concrete request to the right stakeholder (Policy via
  the question-generator) and lists the un-included scenarios as out-of-scope/future candidates.
- Produces a per-workflow summary: examples reviewed (with status), what's included, what's not yet
  included, the reason, and the next action.
