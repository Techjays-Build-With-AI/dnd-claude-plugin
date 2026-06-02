---
description: Produce a client-facing validation pack so stakeholders can confirm or correct Techjays' understanding.
argument-hint: "[module or scope, optional]"
---

Produce a Client Validation Pack for the active project (optionally scoped to: **$ARGUMENTS**).

Delegate to the `validation-agent` subagent. Instantiate
`${CLAUDE_PLUGIN_ROOT}/templates/client-validation-pack.md` and fill it from the knowledge model:
current-state understanding, future-state recommendation, in scope, out of scope, assumptions,
dependencies, open decisions, and questions requiring confirmation.

Rules:
- Only include items mature enough to confirm (Policy 05); clearly mark anything still provisional.
- Make it easy for the client to approve or correct each item.
- Track returned confirmations/corrections into the decision log and update classifications/evidence
  accordingly.

Output the pack file path and a short summary of what the client is being asked to confirm.
