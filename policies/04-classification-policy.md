# 04 — Classification Policy

**Purpose:** force every captured item to declare its epistemic status and route to the right home,
so discovery becomes scope governance rather than note-taking.

Full definitions and worked examples:
[`../reference/classification-taxonomy.md`](../reference/classification-taxonomy.md).

## Rules
1. **No unclassified items.** Anything captured during discovery is tagged as exactly one of: **Fact ·
   Assumption · Decision · Open Question · Risk · Dependency** before it can affect readiness scoring.
2. **Each type has a home** (in the RAID Register unless noted):

   | Type | Home |
   |------|------|
   | Fact | Scope / Architecture document, with an evidence link (Policy 03) |
   | Assumption | RAID → Assumptions |
   | Decision | Decision log (Client Validation Pack) |
   | Open Question | RAID → Open Questions |
   | Risk | RAID → Risks |
   | Dependency | RAID → Dependencies |

3. **Every Open Question gets one sub-class**, which decides whether the module can be estimated:
   *Must close before estimate · Proceed with assumption · Minor implementation detail · Too uncertain
   (exclude / T&M) · Future phase.*
4. **Facts need evidence** (Policy 03); unsupported Facts become Assumptions.
5. **Assumptions surface in the SOW.** A "Ready with Assumptions" verdict lists every assumption the
   estimate relies on, each with its impact-if-wrong.
6. **No duplication.** Items are owned once; documents point to the owner.

## Agent enforcement
- Tags each captured item with a type (and Open Questions with a sub-class) and writes it to the
  correct RAID/Scope location.
- Blocks the readiness gate for any module with an unresolved *Must close before estimate* question.
- Rolls *Too uncertain* and *Future phase* items into the out-of-scope / phasing outputs.
