# Development Workflow

## Purpose

This document is authoritative for how project work moves from an idea to a verified GitHub commit.

## The normal cycle

> **Explain → approve → implement → test → verify → explain → document → commit → push**

Each non-trivial logical step completes the whole cycle before the next dependent step begins.

## 1. Inspect

A minimal read-only preflight may check the path, Git branch and status, recent commits, tracked files, and remote state before reading `AGENTS.md`.

After that preflight, read `AGENTS.md` before substantive status judgments, proposals, or file changes. Then inspect current architecture, roadmap, approved plans, relevant explainers, prior summaries, code, and tests.

Do not infer repository status from conversation alone. Preserve unrelated user changes in a non-clean working tree.

## 2. Explain

Before a non-trivial change, explain:

- the outcome and why the step exists;
- unfamiliar concepts in beginner-friendly terms;
- the recommended approach;
- realistic alternatives and tradeoffs;
- expected files and responsibility changes;
- tests, verification, and known limitations.

## 3. Approve

Wait for explicit approval. Approval applies only to the described scope.

Ask again when a proposed change materially alters architecture, scope, authority boundaries, cost, data handling, or expected outcomes. Do not ask again for ordinary mechanical choices already covered by the approved approach.

## 4. Implement

Make the smallest cohesive approved change. Do not add speculative components, silently resolve open decisions, or refactor unrelated user work.

Do not let an LLM absorb responsibilities assigned to deterministic data, model, policy, scenario, or audit components.

## 5. Test

Tests exercise behavior through repeatable checks. Use the lowest useful level and add integration or end-to-end coverage when risk crosses component boundaries.

For every step, state:

- tests written or run;
- what they prove;
- what they do not prove;
- actual results.

Documentation-only steps use structural and content checks rather than pretending application tests exist.

## 6. Verify

Verification combines test results with broader evidence such as diff inspection, generated-artifact review, data checks, manual behavior review, link validation, or remote-state comparison.

Do not declare success from a command that did not run or from a check whose output was not inspected. Sacred gates require their pre-approved evidence and cannot be waived for convenience.

## 7. Explain and document

Explain what changed, problems encountered, limitations, and the evidence obtained.

Complete the step explainer before the step's final commit. After candidate stage verification, create the retrospective stage summary and rerun final verification with it included.

Follow `docs/documentation-standard.md`. Do not rewrite an approved plan's original decisions after implementation begins.

## 8. Commit

Review the final diff and staged-file list. Confirm that no secrets, generated data, unrelated changes, or out-of-scope files are included.

Each completed logical step receives a focused descriptive commit, for example:

```text
docs(governance): establish project working agreement
feat(data): add raw Home Credit data loader
test(data): verify relational key integrity
```

Avoid vague messages such as `updates`, `fixes`, or `work`.

## 9. Push

A verified, documented commit is normally pushed to `origin` without separate routine authorization once upstream tracking exists.

The first push uses `git push -u origin main`; later pushes use the tracked upstream. Confirm that local `HEAD`, the upstream branch, and GitHub refer to the expected commit.

Stop and request direction for authentication or connectivity failure, unexpected remote history, non-fast-forward state, branch protection, remote mismatch, or another safety concern. Never force-push in the normal workflow.

## Approved stage plans

Before stage implementation, propose and revise the stage plan in conversation. After explicit final approval, save only the final plan as `docs/plans/stage-N-plan.md`, verify it, commit it, and push it.

Raw discussion and intermediate proposals do not belong in the repository.

## Material deviations

When implementation reveals a material problem:

1. stop before the deviation;
2. identify the approved decision and evidence of the problem;
3. explain alternatives, benefits, and costs;
4. wait for approval;
5. preserve the original plan text;
6. document the approved deviation in the step explainer and stage summary;
7. append a labeled amendment to the plan when useful;
8. update `docs/architecture.md` if current architectural truth changes;
9. verify, commit, and push the documentation and implementation coherently.

Minor implementation details that do not alter approved scope or architecture are not material deviations.

## Completion

A step is complete only when implementation, tests, verification, explanation, documentation, commit, and push are complete.

A stage is complete only after its gate passes, its retrospective summary is accurate, final verification passes, all expected commits are pushed, and the working tree and remote state are understood.
