---
description: Render the project knowledge model into a self-contained, read-only HTML report (Client Validation Pack or Final D&D Pack) for client review and print-to-PDF sign-off.
argument-hint: "[validation | final]"
---

Generate an HTML report for the active project. Mode (**$ARGUMENTS**):
- `validation` (default) — the **Client Validation Pack**: current/future state, in/out of scope,
  assumptions, dependencies, open decisions, questions to confirm. For the review round.
- `final` — the **Final D&D Pack**: the full mold, generated only once validation is sufficiently
  complete (Policy 05). For the approval round.

## How to build it
1. Start from `${CLAUDE_PLUGIN_ROOT}/templates/report-template.html`. Keep it **self-contained**
   (inline CSS/JS already included) and **read-only** — do not add any real "Approve" control; the
   plugin has no backend to capture it.
2. Populate from `projects/<active>/knowledge-model.md` (and `inbox/index.md` for evidence links):
   - Replace `{{PROJECT_NAME}}`, `{{CLIENT}}`, `{{PACK_TYPE}}`, `{{VERSION}}`, `{{GENERATED_DATE}}`,
     `{{OVERALL_VERDICT}}`.
   - Inject the readiness rows, per-module cards, RAID rows, and the Approval section into the marked
     `<!-- REGION -->` placeholders, following the inline examples in the template.
   - Render content as **static HTML** (readable with JS disabled). Tag filterable items with
     `data-type` (`in`/`out`/`assumption`/`open`/`risk`) so the filter chips work.
   - For each requirement/assumption, link to its evidence artifact (use the `inbox/index.md` row —
     local path or Drive URL) per the Evidence policy. Show example-coverage as happy/exception/edge
     badges (✓/✗) per `${CLAUDE_PLUGIN_ROOT}/reference/example-coverage.md`.
   - `{{VERSION}}` = the plugin/project version stamp; `{{GENERATED_DATE}}` = today's date.
3. For `final`, include the Approval section verbatim wording (scope-freeze statement, exclusions
   acknowledgement, change-control note) from `${CLAUDE_PLUGIN_ROOT}/policies/01-scope-control-policy.md`
   and a static signatory table.
4. Write to `projects/<active>/outputs/<pack>-<YYYYMMDD>.html` (do not overwrite a prior dated file).

## Honest rendering rules
- Never show a module as "Ready" unless example coverage is 100% and the client has validated it —
  reflect the real gate (`${CLAUDE_PLUGIN_ROOT}/reference/readiness-scoring.md`).
- Items still `needs-fetch` in the index (e.g. un-fetched Drive samples) are shown as gaps, not as
  validated content.

## Tell the user
- Open the file in a browser to review (collapse/filter work there).
- **For sign-off:** Print → Save as PDF — the print stylesheet expands all sections into a clean,
  dated baseline. The Approval Page should cite this exact version + date as the approved baseline.
