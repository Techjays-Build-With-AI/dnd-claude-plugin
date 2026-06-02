---
description: Create a Design & Discovery project shell (name, objective, stakeholders, modules, artifacts, timeline) from the knowledge-model template.
argument-hint: "[project/client name]"
---

Create or resume a D&D project shell for: **$ARGUMENTS**

## Scaffolding is idempotent and non-destructive
Create anything that is **missing**; never overwrite anything that already **exists**. Re-running
`init` on an existing project must resume it, not reset it — a populated `knowledge-model.md` or
`index.md` is real discovery work and must be preserved. For each item below: if absent, create it
from the template; if present, leave it untouched and note "already exists — resuming."

1. **Folder tree** — ensure these exist (create if missing):
   ```
   projects/<slug>/
     inbox/
       .cache/        # fetched copies of remote (Google Drive) artifacts
     outputs/         # generated validation packs / final D&D pack
   ```
   Derive `<slug>` from the project name; if a matching project folder already exists, reuse it.
2. **`knowledge-model.md`** — seed from `${CLAUDE_PLUGIN_ROOT}/templates/project-knowledge-model.md`
   only if absent.
3. **`inbox/index.md`** — seed from `${CLAUDE_PLUGIN_ROOT}/templates/artifact-index.md` only if
   absent. It is the authoritative artifact register; tell the user to add one row per artifact (local
   path or Google Drive link), with its workflow + scenario (happy/exception/edge) where it is an
   example.
4. **`discovery-health-dashboard.md`** — seed from
   `${CLAUDE_PLUGIN_ROOT}/templates/discovery-health-dashboard.md` only if absent.
5. With the user, capture the starting facts: business objective, known stakeholders (with roles),
   candidate modules, the artifacts already available, and the discovery timeline. Append each known
   artifact as a row in `inbox/index.md` (don't duplicate rows that are already there).
6. Classify any captured items per `${CLAUDE_PLUGIN_ROOT}/reference/classification-taxonomy.md` and
   record sources per the Evidence policy.

Do not invent details the user has not provided — mark unknowns as Open Questions. Finish by
reporting what was created vs already present, and listing what artifacts/examples to gather next.
