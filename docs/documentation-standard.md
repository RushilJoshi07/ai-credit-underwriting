# Documentation Standard

## Purpose

Documentation preserves requirements, reasoning, evidence, limitations, and history so a fresh session can understand the project without old conversations.

Documents should be concise enough to maintain but complete enough to defend engineering decisions. Do not duplicate large normative sections when a summary and link are sufficient.

## Document authority

- `AGENTS.md` governs Codex behavior.
- `docs/architecture.md` governs current architecture.
- `docs/project-roadmap.md` governs major stage sequence and dependencies.
- `docs/plans/stage-N-plan.md` preserves approved original stage intent.
- `docs/development-workflow.md` governs the engineering lifecycle.
- This document governs documentation lifecycle and content.
- `docs/interview-learning-standard.md` governs teaching and interview content.
- `docs/zero-cost-constraints.md` governs cost eligibility.
- Step explainers record actual step implementation and evidence.
- Stage summaries record actual stage outcomes and inherited assumptions.
- `README.md` is a human-oriented summary, not a replacement for authoritative documents.

If authoritative documents genuinely conflict, do not silently choose one. Inspect Git history and approved deviations, then request clarification or propose an explicit correction.

## Approved stage plans

Each major stage requires one final approved plan:

```text
docs/plans/stage-N-plan.md
```

Before proposing it, inspect repository state, architecture, roadmap, previous plans, relevant explainers, previous summaries, code, and tests.

The plan must be proposed and revised outside the repository. After explicit final approval, save only the approved version, verify it, commit it, and push it before implementation.

It should normally include:

- context and repository state entering the stage;
- objective and inherited dependencies;
- in-scope and out-of-scope work;
- design decisions and realistic alternatives;
- reasons alternatives were rejected or deferred;
- step order and expected deliverables;
- verification strategy and stage gate;
- decisions locked for the stage;
- decisions still open;
- assumptions the next stage may inherit.

Do not commit raw conversations, intermediate proposals, or external review discussion.

## Preserving original intent

After implementation begins, do not rewrite original plan decisions to resemble later execution.

A material deviation requires prior explanation and approval. Record it in the relevant step explainer and final stage summary. When useful, append a clearly labeled approved amendment or deviation section to the plan without replacing the original text. Update architecture when current architectural truth changes.

This preserves a useful distinction:

- the plan says what was intended;
- the explainer says how a step was implemented;
- the summary says what the stage actually achieved;
- architecture says what is currently true.

## Step explainers

Store meaningful step explainers under:

```text
docs/explanations/stage-N/
```

Use a descriptive lowercase hyphenated name. Each explainer must contain sections equivalent to:

1. What this step does
2. Why this step exists
3. What existed before
4. What exists afterward
5. Files created or modified
6. Architecture and data-flow walkthrough
7. Important implementation explained
8. New concepts introduced
9. Design decisions
10. Why this approach
11. Alternatives considered
12. Why alternatives were rejected or deferred
13. Tests written
14. What the tests prove
15. What the tests do not prove
16. Verification results
17. Problems encountered
18. How they were solved
19. Interview questions and strong answers
20. Hard or senior-level interview questions
21. What comes next and why

Equivalent headings may fit the step better, but substantive content must not be silently omitted. If a category does not apply, state why. Do not invent tests, results, or problems.

Complete the explainer before the step's final commit.

## Stage summaries

After candidate stage verification has actually run, create a retrospective summary under the stage's explanation directory.

It must record:

- stage objective;
- completed steps;
- component interactions;
- major design decisions;
- approved deviations from the plan;
- verification gate and actual evidence;
- what was proven;
- what was not proven;
- remaining limitations;
- final test status;
- interview defense;
- final outcome;
- dependencies and assumptions the next stage may safely inherit.

Run final verification after the summary exists. A stage is not complete until its accurate summary is committed and pushed.

## Current and historical documents

Plans and explainers are historical records and should not be rewritten to erase original intent or actual outcomes. Corrections should be clearly labeled when material.

Architecture, roadmap, workflow, standards, constraints, and README describe current project truth and should be updated through approved changes when that truth changes.

Code and tests provide executable evidence. If they disagree with current documentation, treat the mismatch as a defect rather than allowing silent drift.

## Linking and traceability

- Use repository-relative links.
- Link summaries to their approved plan and relevant explainers.
- Link explainers to authoritative decisions instead of copying them.
- Identify model, data, policy, source, or schema versions when those artifacts exist.
- Keep fictional and authoritative materials clearly labeled.

## Writing quality

- Distinguish implemented, planned, provisional, open, and unsupported claims.
- Explain unfamiliar concepts in plain language.
- Record reasons and tradeoffs, not only outcomes.
- State what evidence proves and does not prove.
- Avoid claims of compliance, certification, production readiness, or real-lending suitability.
- Keep terminology consistent with architecture and roadmap.
- Do not call Home Credit `TARGET` default until authoritative documentation supports approved terminology.

## Documentation verification

Before completion:

- check required files and headings;
- validate relative links and referenced paths;
- run `git diff --check`;
- inspect the full diff and staged-file list;
- check repeated terms and responsibility boundaries for consistency;
- confirm no placeholder results or unimplemented capability claims remain;
- verify that approved plans preserve original text;
- confirm retrospective claims are based on actual evidence.

## Fresh-session path

After a minimal read-only repository preflight, reconstruct context through:

```text
AGENTS.md
→ docs/architecture.md
→ docs/project-roadmap.md
→ approved docs/plans/
→ step explainers
→ stage summaries
→ implementation and tests
→ Git history when needed
```
