---
description: Ingest discovery artifacts (transcripts, notes, documents, samples, screenshots) into categorized, classified, source-traced discovery notes.
argument-hint: "[paths or description of artifacts]"
---

Ingest the discovery material for the active project: **$ARGUMENTS**

Delegate the heavy extraction to the `intake-agent` subagent. It should return structured output:
categorized notes, and extracted entities, workflows, business rules, risks, and open questions.

Then, in the project knowledge model:
1. **Classify every extracted item** as Fact / Assumption / Decision / Open Question / Risk /
   Dependency per `${CLAUDE_PLUGIN_ROOT}/reference/classification-taxonomy.md`. Open Questions get a
   sub-class.
2. **Record the source** of each item (which artifact/interview) and a confidence + validation status
   per `${CLAUDE_PLUGIN_ROOT}/policies/03-evidence-and-traceability-policy.md`. A Fact with no source
   is downgraded to an Assumption.
3. Note which artifacts are **examples** and tag their scenario type (happy / exception / edge) toward
   example coverage.

Report what was ingested, what was classified, and what is still missing (e.g. only happy-path
samples received).
