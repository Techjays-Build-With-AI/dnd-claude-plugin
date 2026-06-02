# The D&D Mold — Human-Readable Schema

This is the readable companion to [`dnd-schema.yaml`](./dnd-schema.yaml), which is the machine
source of truth. It mirrors `00 - D&D Document Guide.xlsx`. **Do not add sections that are not in
the workbook** — if the business needs a new section, change the workbook first, then re-encode.

## The pack at a glance

The D&D pack is the *Scope & Agreement + Solution & Plan* artifact set produced in lifecycle phases
2–4 (Scoping, Solutioning, Planning & Prepare) of the **Excellence Command Center**. It is the
evidence base the **PSRC** (Project Solution Review Committee) reviews before execution starts.

> Each document answers one question, has one owner, and earns one sign-off.

| # | Document | Question it answers | Owner | Approves (sign-off) |
|---|----------|---------------------|-------|---------------------|
| 1 | Executive Summary / Engagement Brief | Why are we doing this, what outcome, what's recommended? | Engagement lead | Orientation & recommended approach |
| 2 | Scope Document (incl. Requirements) | What are we building? What's in / out? What are the rules? | BA / Engagement lead | The scope-freeze baseline |
| 3 | Technical Architecture & Solution Design | How will it work technically? AI vs deterministic, data, integrations, NFRs? | Architect / Tech lead | Technical feasibility |
| 4 | RAID Register | Under what conditions does this estimate hold? | Engagement lead | The conditions attached to the price |
| 5 | Implementation Plan & Phasing | In what order and over what timeline (Learn/Proof/Ship/Evolve)? | Delivery lead | Sequencing & phasing |
| 6 | Approval / Sign-off Page | Is this baseline agreed by the client? | Client signatories + PSRC | The scope freeze itself |

## The PSRC review lenses

The internal gate. Readiness verdicts ([readiness.md](./readiness-scoring.md)) report against these:

1. **Solution Fit** · 2. **Scope Completeness** · 3. **Architecture Soundness** ·
4. **Risk & Feasibility** · 5. **Effort & Timeline** · 6. **Value & ROI** · 7. **Client Impact**

PSRC approval is *Approve to Proceed → Execution Starts*.

## Document 1 — Executive Summary / Engagement Brief
*Often the only document a sponsor reads end-to-end. Short and decision-oriented.*
Engagement context & business driver · Current-state summary · Future-state vision ·
Recommended approach · Scope at a glance · Commercial-model note · Headline risks & assumptions ·
Decision requested.

## Document 2 — Scope Document (the thing that gets frozen)
**Document-level:** Scope statement · Module breakdown · AI-vs-deterministic responsibility split ·
User roles & permissions · Global out-of-scope · Assumptions reference (→ RAID).

**Per module** (repeated for each module in the breakdown):
Current state · Future state · In scope / Out of scope · Functional requirements · Business rules ·
Exceptions · Data fields · Integrations · Acceptance criteria.

> Requirements here are at module/capability level — the detailed SRS comes later in build.

## Document 3 — Technical Architecture & Solution Design
Solution overview & context diagram · Component architecture · AI/ML approach ·
Deterministic logic boundary · Data architecture & dictionary · Integration specifications · NFRs ·
Security & compliance · Environments & deployment · Technical constraints ·
Responsible AI & guardrails · Monitoring & drift (Evolve).

## Document 4 — RAID Register (the conditions the price depends on)
Assumptions · Dependencies · Risks · Open questions · Open-question classification ·
Resolution log / status.

## Document 5 — Implementation Plan & Phasing
Phase breakdown (Learn → Proof → Ship → Evolve) · Module-to-phase mapping · Milestones &
deliverables · Sequencing & dependencies · Timeline view · Resource & cost plan ·
Communication plan · Quality & acceptance plan · Entry/exit criteria per phase.

## Document 6 — Approval / Sign-off Page (two gates)
Scope-freeze statement · What is being approved · Exclusions acknowledgement ·
Internal PSRC review & approval · Change-control note · Signatory table.

The **change-control note** is fixed wording — see [Scope Control Policy](../policies/01-scope-control-policy.md).
