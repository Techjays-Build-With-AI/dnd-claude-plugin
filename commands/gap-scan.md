---
description: Fill the D&D mold from captured info, score scope readiness and example coverage per module, and list every gap.
argument-hint: "[module name, optional]"
---

Run a completeness scan for the active project (optionally just module: **$ARGUMENTS**).

Delegate to the `gap-detector` subagent. It compares the required schema
(`${CLAUDE_PLUGIN_ROOT}/reference/dnd-schema.yaml`) against captured info and returns gaps.

Produce:
1. **Schema fill status** per document/section — Captured / Partial / Weak / Missing, with confidence.
2. **Per-module Scope Readiness Score** and **example-coverage score** per
   `${CLAUDE_PLUGIN_ROOT}/reference/readiness-scoring.md`.
3. **Gap list:** missing sections, weakly supported requirements, unconfirmed assumptions, unmapped
   exceptions, missing stakeholders, missing samples, missing integration details.
4. The **next action** for each significant gap (who to ask / what example to request).

Apply the gates: a module is not "Ready for fixed-bid" unless example coverage is 100% and the client
has validated it. Update the Discovery Health Dashboard.
