# Scope Readiness Scoring

The agent never asserts "this is scoped." It computes a **Scope Readiness Score** per module and a
verdict per engagement, and reports the evidence behind both. This file defines how.

## 1. Per-module dimensions

Each module in the Scope Document is scored 0–100% on each dimension. A dimension's score reflects
*how completely and how credibly* it is captured — backed by evidence, not just written down.

| Dimension | What "high" means |
|-----------|-------------------|
| Current state | Actors, triggers, inputs/outputs, systems, manual steps, pain points, known exceptions captured and traced to artifacts. |
| Future state | AI role, automation role, human approval points, exception flow, audit trail defined. |
| Business rules | Approval/matching/validation/escalation rules confirmed, ideally from real examples. |
| Exceptions | Exception cases enumerated and handling defined. |
| Data fields | Inputs/outputs and read/write fields identified. |
| Integrations | Systems, direction, protocol, auth, constraints identified. |
| Acceptance criteria | Measurable completion criteria derived. |
| **Example coverage** | Workflow walked through with real client examples — see [example-coverage.md](./example-coverage.md). |
| Sign-off | Client has validated the interpretation. |

The composite **Scope Readiness Score** is the (optionally weighted) blend of these dimensions.
Example coverage and sign-off are **gating**: a module cannot be called "Ready" while either is low,
regardless of the blend — see the gate below.

## 2. Readiness thresholds → commit recommendation

| Score | Recommendation |
|-------|----------------|
| 80%+ | Ready for fixed-bid scope discussion |
| 60–79% | Needs clarification before fixed bid |
| 40–59% | Keep as assumption-heavy or future phase |
| Below 40% | Exclude from fixed bid or move to T&M |

## 3. The example-coverage gate (hard rule)

Example coverage is scored from the three required example types:

| Example coverage | Decision |
|------------------|----------|
| 100% (happy + exception + edge) | Ready for scope baseline |
| 67% (two of three) | Can estimate with explicit assumptions |
| 33% (one of three) | Not ready for fixed bid |
| 0% | Exclude or keep as future discovery |

**Gate:** a module may not be reported as "Ready for fixed-bid" unless example coverage is 100% **and**
the client has validated the interpretation. This is the primary anti-scope-creep control. See the
[Example-Based Validation Policy](../policies/02-example-based-validation-policy.md).

## 4. Mapping scores → the PSRC lenses

The engagement-level readiness verdict reports against the seven PSRC lenses so it drops straight
into the governance gate:

| PSRC lens | Fed primarily by |
|-----------|------------------|
| Solution Fit | Future-state quality across modules; AI-vs-deterministic split. |
| Scope Completeness | Schema fill rate; example coverage; count of unmapped exceptions. |
| Architecture Soundness | Technical Architecture document completeness; integration specs. |
| Risk & Feasibility | RAID register depth; high-impact open assumptions; unvalidated dependencies. |
| Effort & Timeline | Implementation Plan resource/cost plan; modules ready vs deferred. |
| Value & ROI | Executive Summary business driver + future-state vision. |
| Client Impact | Sign-off status; exclusions acknowledged; change-control understood. |

## 5. Engagement verdict

The readiness agent returns one of:

- **Ready** — enough modules pass the gate to commit a fixed bid; no blocking open questions.
- **Ready with Assumptions** — committable if specific named assumptions are written into the SOW
  and specific risks get commercial protection.
- **Not Ready** — blocking gaps; lists exactly which modules to exclude, defer, or move to T&M, and
  what evidence would change the verdict.

Every verdict must state **which modules are ready, which to exclude, which are future-phase, which
assumptions must enter the SOW, and which risks need commercial protection** — never a bare verdict.
