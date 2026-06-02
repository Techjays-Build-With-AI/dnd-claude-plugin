---
description: Create a Design & Discovery project shell (name, objective, stakeholders, modules, artifacts, timeline) from the knowledge-model template.
argument-hint: "[project/client name]"
---

Create a new D&D project shell for: **$ARGUMENTS**

1. Create `projects/<slug>/` in the current working directory.
2. Instantiate `${CLAUDE_PLUGIN_ROOT}/templates/project-knowledge-model.md` there as
   `knowledge-model.md`.
3. With the user, capture the starting facts: business objective, known stakeholders (with roles),
   candidate modules, the list of artifacts already available, and the discovery timeline.
4. Seed an empty Discovery Health Dashboard from `${CLAUDE_PLUGIN_ROOT}/templates/discovery-health-dashboard.md`.
5. Classify any captured items per `${CLAUDE_PLUGIN_ROOT}/reference/classification-taxonomy.md` and
   record sources per the Evidence policy.

Do not invent details the user has not provided — mark unknowns as Open Questions. Finish by listing
what artifacts/examples to gather next.
