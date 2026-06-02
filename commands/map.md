---
description: Convert ingested discovery notes into current-state and future-state workflows per module.
argument-hint: "[module name, optional]"
---

Map workflows for the active project (optionally just module: **$ARGUMENTS**).

Delegate to the `workflow-mapper` subagent. For each module, produce:
- **Current state:** actors, triggers, inputs/outputs, systems, manual steps, pain points, known
  exceptions.
- **Future state:** AI role, deterministic software role, human approval points, exception flow,
  system updates, audit trail.
- Decision points and AI opportunities.

Ground every workflow step in real client examples where available
(`${CLAUDE_PLUGIN_ROOT}/reference/example-coverage.md`). Flag steps that are described but not yet
evidenced by an example as Open Questions. Write results into the project knowledge model.
