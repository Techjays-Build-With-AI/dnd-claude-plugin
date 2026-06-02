---
description: Judge whether scope is ready for a fixed-bid proposal — Ready / Not Ready / Ready-with-Assumptions, reported against the seven PSRC lenses.
argument-hint: "[module or whole engagement, optional]"
---

Assess fixed-bid readiness for the active project (optionally scoped to: **$ARGUMENTS**).

Delegate to the `readiness-agent` subagent. Using the readiness model
(`${CLAUDE_PLUGIN_ROOT}/reference/readiness-scoring.md`), return:

1. **Engagement verdict:** Ready / Ready with Assumptions / Not Ready.
2. **Per-PSRC-lens assessment** (Solution Fit, Scope Completeness, Architecture Soundness, Risk &
   Feasibility, Effort & Timeline, Value & ROI, Client Impact).
3. **Module disposition:** which modules are ready, which to exclude, which to defer to a future phase,
   which to move to T&M.
4. **SOW conditions:** assumptions that must be written into the SOW; risks that need commercial
   protection.
5. **What would change the verdict:** the specific evidence/validation still needed.

Never return a bare verdict. Apply the example-coverage + client-validation gate before calling any
module "Ready."
