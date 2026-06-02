---
description: Ingest discovery artifacts (transcripts, notes, documents, samples, screenshots) into categorized, classified, source-traced discovery notes.
argument-hint: "[paths or description of artifacts]"
---

Ingest the discovery material for the active project: **$ARGUMENTS**

## 0. Resolve artifacts via the index (do this first)

If `projects/<active>/inbox/index.md` exists, treat it as the **authoritative artifact register**.
Otherwise ingest the paths in `$ARGUMENTS` directly (and offer to create an index from them).

For each row in the index:
- **`local`** → confirm the path is readable; mark `Status: ready`.
- **`gdrive`** → fetch it before the subagent runs. The subagents can only read local files, so YOU
  (the orchestrator) fetch each Google Drive item using the **`claude.ai Google Drive` MCP tools**
  (discover them via ToolSearch; if the connector is not yet authorized, run
  `mcp__claude_ai_Google_Drive__authenticate`, share the URL with the user, and stop until authorized).
  Save each fetched file into `projects/<active>/inbox/.cache/`, then update that row's `Local path`
  and set `Status: ready`. Keep the original Drive URL as the provenance/source.
- Anything that cannot be fetched stays `needs-fetch` and is reported as a gap — it is **not** ingested
  and does **not** count toward example coverage or validation.

Then delegate the heavy extraction to the `intake-agent` subagent, passing it the resolved **local
paths** (originals + `.cache/` copies) and their index IDs. It returns structured output: categorized
notes, and extracted entities, workflows, business rules, risks, and open questions.

Then, in the project knowledge model:
1. **Classify every extracted item** as Fact / Assumption / Decision / Open Question / Risk /
   Dependency per `${CLAUDE_PLUGIN_ROOT}/reference/classification-taxonomy.md`. Open Questions get a
   sub-class.
2. **Record the source** of each item (which artifact/interview) and a confidence + validation status
   per `${CLAUDE_PLUGIN_ROOT}/policies/03-evidence-and-traceability-policy.md`. A Fact with no source
   is downgraded to an Assumption.
3. Note which artifacts are **examples** and tag their scenario type (happy / exception / edge) toward
   example coverage. Use the index's `Workflow` + `Scenario` columns as the mapping.
4. Update each ingested row's `Status` to `ingested` in `inbox/index.md`.

Report what was ingested, what was classified, what is still **`needs-fetch`** (e.g. Drive items not
yet authorized/reachable), and what example types are still missing per workflow.
