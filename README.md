# Techjays D&D Co-Pilot (`dnd-copilot`)

A Claude Code **plugin** that turns Techjays' Design & Discovery (D&D) document guide into an active
**scope-governance assistant**. It treats the D&D mold as a schema, ingests interviews/documents/
samples, maps them into the required discovery outputs, scores scope readiness, enforces
example-based validation, generates stakeholder questions, and produces a validated scope baseline for
fixed-bid proposals.

> The mold is the required shape. Client artifacts are raw material. The agent is the inspector.
> The frozen scope is the cast output. The one question it always answers:
> **"Can we safely estimate and commit to this scope?"**

## Why

Techjays historically suffered **scope creep** — committing against a happy-path understanding, then
hitting exceptions and edge cases during build. This plugin enforces the discipline that prevents
that: nothing is "scope-ready" without validated real client examples, every item is classified and
sourced, and readiness is scored and reported, never asserted.

## Names at a glance

This one Git repo is both the **marketplace** and the **plugin** it contains:

| Thing | Value | Where it comes from |
|-------|-------|---------------------|
| Marketplace name | `techjays-mp` | `.claude-plugin/marketplace.json` → `name` |
| Plugin name | `dnd-copilot` | `.claude-plugin/plugin.json` → `name` |
| Install identifier | `dnd-copilot@techjays-mp` | `<plugin>@<marketplace>` |
| Command namespace | `/dnd-copilot:<command>` | the plugin name |

## What's inside

| Path | Purpose |
|------|---------|
| `policies/` | Dual-use governance (human-readable + agent-enforced). Start at `00-scope-governance-charter.md`. |
| `reference/` | The encoded mold (`dnd-schema.yaml`/`.md`), readiness scoring, classification taxonomy, example-coverage rules. |
| `skills/discovery-completeness/` | The core orchestrator skill — auto-triggers on D&D/discovery work and runs the loop. |
| `commands/` | One slash command per stage: `init · intake · map · gap-scan · questions · validation-pack · readiness · report`. |
| `agents/` | Seven subagents that do the heavy lifting per stage. |
| `templates/` | Output shapes: artifact index, knowledge model, health dashboard, client validation pack, workflow example validation, and a self-contained HTML report. |

The plugin is the tool; per-project knowledge bases are generated into **your** working directory
under `projects/<client>/`. Source of truth for the mold is `reference/dnd-schema.yaml`.

---

## Step 1 — Publish the repo to GitHub (one-time, done by the maintainer)

The whole folder is the plugin **and** the marketplace, so you publish it as a single repo. From the
project root (`D:\Projects\TechJays\DnD`):

```bash
git init
git add .
git commit -m "Initial D&D co-pilot plugin"
# the empty repo already exists at github.com/Techjays-Build-With-AI/dnd-claude-plugin
git remote add origin https://github.com/Techjays-Build-With-AI/dnd-claude-plugin.git
git branch -M main
git push -u origin main
```

The marketplace is discovered automatically because `.claude-plugin/marketplace.json` lives at the
repo root. For a **private** repo, make sure each teammate's `git`/`gh` is authenticated to GitHub so
Claude Code can clone it (e.g. `gh auth login`).

> Repo naming: the repo name (`dnd-claude-plugin`) is independent of the marketplace name — Claude
> Code reads the marketplace's `name` field (`techjays-mp`) from `marketplace.json`, not the repo name.

## Step 2 — Add the marketplace and install the plugin (each teammate)

In Claude Code:

```text
/plugin marketplace add Techjays-Build-With-AI/dnd-claude-plugin
/plugin install dnd-copilot@techjays-mp
```

`/plugin marketplace add` accepts the GitHub `owner/repo` shorthand, a full `https://…git` URL, or a
local path. Note the two names differ on purpose: you **add the marketplace by repo**
(`Techjays-Build-With-AI/dnd-claude-plugin`) but **install the plugin by its marketplace identity**
(`dnd-copilot@techjays-mp`). After installing, restart Claude Code (or run `/reload-plugins`) if the
commands don't appear immediately.

**Verify it loaded:**
- `/help` lists the `/dnd-copilot:*` commands and the `discovery-completeness` skill.
- `/agents` lists the seven subagents (`intake-agent`, `workflow-mapper`, `scope-structurer`,
  `gap-detector`, `question-generator`, `validation-agent`, `readiness-agent`).

### Optional: auto-install for the whole team

Commit a project `.claude/settings.json` (in the *client-work* repo where teams run discovery, not in
this plugin repo) so teammates are prompted to install automatically when they trust the repo:

```json
{
  "extraKnownMarketplaces": {
    "techjays-mp": {
      "source": { "source": "github", "repo": "Techjays-Build-With-AI/dnd-claude-plugin" }
    }
  },
  "enabledPlugins": {
    "dnd-copilot@techjays-mp": true
  }
}
```

(The `extraKnownMarketplaces` key must be the marketplace `name` — `techjays-mp` — while `repo` points
at the GitHub repo that hosts it.)

### Updating later

When the maintainer pushes changes (e.g. a new schema version), teammates run:

```text
/plugin marketplace update techjays-mp
/plugin install dnd-copilot@techjays-mp
```

---

## Step 3 — Use it on a discovery engagement

Work from the directory where you want the project's knowledge base to live (the plugin writes into
`projects/<client>/` there). You can drive it two ways.

**A. Just describe the work** — the `discovery-completeness` skill triggers automatically:

> "I'm starting discovery for Acme's accounts-payable automation. Here are the interview notes and
> three sample invoices — help me scope it."

**B. Drive the stages explicitly** with the slash commands, in order:

| Step | Command | What it does |
|------|---------|--------------|
| 1 | `/dnd-copilot:init Acme AP Automation` | Create the project shell (objective, stakeholders, modules, artifacts, timeline). |
| 2 | `/dnd-copilot:intake ./notes ./samples` | Ingest transcripts/notes/documents/samples; classify and source every item. |
| 3 | `/dnd-copilot:map` | Build current-state and future-state workflows per module. |
| 4 | `/dnd-copilot:gap-scan` | Fill the mold, score readiness + example coverage, list every gap. |
| 5 | `/dnd-copilot:questions` | Generate stakeholder questions and example requests for the gaps. |
| 6 | `/dnd-copilot:validation-pack` | Produce the client-facing confirmation pack. |
| 7 | `/dnd-copilot:readiness` | Verdict — Ready / Not Ready / Ready-with-Assumptions vs the 7 PSRC lenses. |
| 8 | `/dnd-copilot:report [validation\|final]` | Render the knowledge model into a self-contained, read-only HTML report for client review + print-to-PDF sign-off. |

You can enter at any step depending on what you already have, and re-run `gap-scan` / `readiness` as
new evidence arrives. The co-pilot will **refuse to call a workflow scope-ready** until it has a
validated happy-path, exception, and edge example for it — that gate is the whole point.

### Artifacts: local + Google Drive (the artifact index)

`init` scaffolds `projects/<client>/inbox/index.md` — the authoritative register of every artifact.
Add one row per file with its access type and (for examples) its workflow + scenario:

| ID | Access | Location | Workflow | Scenario | Status |
|----|--------|----------|----------|----------|--------|
| A1 | local | inbox/kickoff.txt | — | — | ready |
| A3 | gdrive | https://drive.google.com/file/d/abc123 | Invoice Validation | happy | needs-fetch |

- **`local`** files are read directly.
- **`gdrive`** files are fetched automatically: on `intake`, the orchestrator pulls each Drive item via
  the **Google Drive connector** into `inbox/.cache/`, marks it `ready`, and keeps the Drive URL as
  provenance. The first time, it will ask you to authorize the connector (a one-time OAuth link).
- Anything it can't reach stays `needs-fetch` and is reported as a gap — it does **not** count toward
  example coverage or readiness. So a workflow whose exception sample is still stuck in Drive shows as
  *not* scope-ready, with "fetch A4 from Drive" as the next action.

### What you get out
- `projects/<client>/knowledge-model.md` — the living source of truth.
- A continuously updated **Discovery Health Dashboard** (internal).
- A **Client Validation Pack** when sections mature.
- A **readiness verdict** mapped to the PSRC review lenses, and eventually the **Final D&D Pack**.
- A self-contained **HTML report** (`/dnd-copilot:report`) for client review — collapsible modules,
  clickable evidence/example traceability, the readiness + coverage gates visualized. It is
  **read-only**: sign-off is by a dated **print-to-PDF** export of that exact version, cited on the
  Approval Page (no fake in-page "Approve" button — the plugin has no backend to capture one). The
  content is static HTML, so it stays readable even if a mail client strips JavaScript.

---

## Updating the mold

The schema mirrors `00 - D&D Document Guide.xlsx`. If the business changes the workbook, re-encode
`reference/dnd-schema.yaml` (and the `.md` companion), bump `version` in
`.claude-plugin/plugin.json` and `.claude-plugin/marketplace.json`, and push. Do **not** add sections
to the schema that aren't in the workbook.
