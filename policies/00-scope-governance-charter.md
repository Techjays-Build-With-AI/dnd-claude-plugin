# 00 — Scope Governance Charter

**Audience:** everyone on a Techjays Design & Discovery engagement — and the D&D co-pilot agent,
which enforces these policies.
**Status:** governing document. The policies in this folder are dual-use: humans follow them; the
agent enforces them.

## Why this exists

Techjays reimagines client workflows with AI. We do that through a **Design & Discovery (D&D)** phase:
interview stakeholders, review artifacts, ask the right questions, and detail the scope. Historically
we have suffered **scope creep** — committing to a price against a "happy-path" understanding, then
discovering exceptions, document variations, and hidden approvals during build.

This charter and its policies exist to make every D&D engagement produce an outcome we can confidently
say: **gathers all requirements, explicitly specifies what is in and out of scope, and records its
assumptions** — backed by evidence.

## The mental model

| Element | Role |
|---------|------|
| The D&D Document Guide (`00 - D&D Document Guide.xlsx`) | The **mold** — the required shape of the outcome. Encoded in [`../reference/dnd-schema.yaml`](../reference/dnd-schema.yaml). |
| Client artifacts, interviews, samples, transcripts | The **raw material**. |
| The D&D co-pilot agent | The **inspector** — fills the mold, finds gaps, demands evidence. |
| The approved, frozen scope | The **cast output**. |

The agent does not just ask *"Is the mold filled?"* It asks *"Has every part of the mold been tested
with real client examples, validated by the client, and is anything still assumed or risky before we
estimate?"*

## The one question

Every output answers a single governing question:

> **Can we safely estimate and commit to this scope?**

Not "can we generate a document?" That distinction is the whole point.

## How this fits the Excellence Command Center

The D&D pack is produced in lifecycle phases 2–4 (Scoping, Solutioning, Planning & Prepare) and is the
evidence base the **PSRC** (Project Solution Review Committee) reviews before execution starts. PSRC
approval is the internal *Approve to Proceed → Execution Starts* gate; client sign-off freezes the
scope baseline for the fixed-bid proposal. The agent's readiness verdict reports against the seven
PSRC lenses (see [`../reference/readiness-scoring.md`](../reference/readiness-scoring.md)).

## The policies

| # | Policy | In one line |
|---|--------|-------------|
| 01 | [Scope Control](./01-scope-control-policy.md) | What's scoped = what was reviewed and approved; everything else is change control. |
| 02 | [Example-Based Validation](./02-example-based-validation-policy.md) | No workflow is scoped without real client examples (happy + exception + edge). |
| 03 | [Evidence & Traceability](./03-evidence-and-traceability-policy.md) | Every requirement and assumption traces to a source. |
| 04 | [Classification](./04-classification-policy.md) | Every item is a Fact / Assumption / Decision / Open Question / Risk / Dependency. |
| 05 | [Completeness & Sign-off](./05-completeness-and-signoff-policy.md) | When a module is "mature," what we produce, and how we freeze. |

## Non-negotiables (summary)
1. Nothing is "scope-ready" without validated real-world examples.
2. Every Fact has a source; an unsupported Fact is downgraded to an Assumption.
3. Every item is classified; assumptions surface in the SOW.
4. Readiness is scored and reported, never asserted.
5. Anything not reviewed and validated in D&D is **out of scope** until added via change control.
