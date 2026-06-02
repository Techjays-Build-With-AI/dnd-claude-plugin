---
description: Create a Design & Discovery project shell (name, objective, stakeholders, modules, artifacts, timeline) from the knowledge-model template.
argument-hint: "[project/client name]"
---

Create a new D&D project shell for: **$ARGUMENTS**

1. Create `projects/<slug>/` in the current working directory, with an `inbox/` subfolder for raw
   artifacts (and `inbox/.cache/` for fetched remote files).
2. Instantiate `${CLAUDE_PLUGIN_ROOT}/templates/project-knowledge-model.md` there as
   `knowledge-model.md`.
3. Instantiate `${CLAUDE_PLUGIN_ROOT}/templates/artifact-index.md` as `inbox/index.md` — the
   authoritative artifact register. Tell the user to add one row per artifact (local path or Google
   Drive link), with its workflow + scenario (happy/exception/edge) where it is an example.
4. With the user, capture the starting facts: business objective, known stakeholders (with roles),
   candidate modules, the list of artifacts already available, and the discovery timeline. Record
   each known artifact as a row in `inbox/index.md`.
5. Seed an empty Discovery Health Dashboard from `${CLAUDE_PLUGIN_ROOT}/templates/discovery-health-dashboard.md`.
6. Classify any captured items per `${CLAUDE_PLUGIN_ROOT}/reference/classification-taxonomy.md` and
   record sources per the Evidence policy.

Do not invent details the user has not provided — mark unknowns as Open Questions. Finish by listing
what artifacts/examples to gather next.
