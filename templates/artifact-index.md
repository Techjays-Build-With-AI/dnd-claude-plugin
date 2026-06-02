# Artifact Index — <PROJECT/CLIENT NAME>

> The authoritative register of every discovery artifact: where it lives, what it's for, and whether
> it has actually been ingested. This is also the evidence source-of-record (Policy 03) — every
> requirement traces back to an artifact ID here. The example-coverage mapping (happy / exception /
> edge) is driven by the `Workflow` + `Scenario` columns.

## How to use
- Add one row per artifact. `ID` is a stable handle (A1, A2, …) used as the evidence reference.
- **Access** = how the plugin reaches it: `local` (a path it can read) or `gdrive` (a Google Drive
  link/ID it must fetch first).
- **Status** lifecycle: `needs-fetch` → `ready` (ingestible) → `ingested`. Anything not `ready`/
  `ingested` does **not** count toward example coverage or validation.
- For `gdrive` items, the orchestrator fetches them via the Google Drive connector into
  `inbox/.cache/` and updates `Local path` + `Status`; the Drive URL stays as provenance.

## Register

| ID | Artifact | Access | Location (URL or path) | Local path (after fetch) | Type | Workflow | Scenario | Status |
|----|----------|--------|------------------------|--------------------------|------|----------|----------|--------|
| A1 | Kickoff transcript | local | inbox/kickoff.txt | inbox/kickoff.txt | transcript | — | — | ready |
| A2 | AP process notes | local | inbox/ap-notes.md | inbox/ap-notes.md | notes | Invoice Intake | — | ready |
| A3 | Invoice INV-1045 | gdrive | https://drive.google.com/file/d/abc123 | | sample (PDF) | Invoice Validation | happy | needs-fetch |
| A4 | Missing-PO invoice | gdrive | https://drive.google.com/file/d/def456 | | sample (PDF) | Invoice Validation | exception | needs-fetch |
| A5 | Credit-memo email thread | gdrive | https://drive.google.com/file/d/ghi789 | | email | Invoice Validation | edge | needs-fetch |

**Type** examples: transcript · notes · sample · email · screenshot · report · spreadsheet · existing-spec.
**Scenario** (for workflow examples): `happy` · `exception` · `edge` · `—` (not an example).

## Coverage rollup (maintained by gap-scan)
| Workflow | Happy | Exception | Edge | Coverage % |
|----------|:-----:|:---------:|:----:|-----------:|
| | | | | |
