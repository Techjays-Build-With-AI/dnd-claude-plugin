---
description: Generate stakeholder-specific clarification questions and example requests for every open gap.
argument-hint: "[stakeholder or module, optional]"
---

Generate clarification questions for the active project (optionally scoped to: **$ARGUMENTS**).

Delegate to the `question-generator` subagent. From the current gaps and open questions, produce
question sets grouped by stakeholder type (Business, IT, Compliance, Data, Exception-handling,
Approval/sign-off) and by module.

Rules:
- For every workflow short of 100% example coverage, generate an **example request** — ask for
  specific real cases (one normal, one exception, one complex), not just answers
  (`${CLAUDE_PLUGIN_ROOT}/reference/example-coverage.md`).
- Prioritise questions that close *Must-close-before-estimate* open questions
  (`${CLAUDE_PLUGIN_ROOT}/reference/classification-taxonomy.md`).
- Phrase questions in the stakeholder's terms and tie each to the gap it closes.

Output a ready-to-send question list per stakeholder.
