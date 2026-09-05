# Step 0 Explainer — Project Governance and Architecture Foundation

## 1. What this step does

This step turns the approved Stage 0 plan into the repository's working governance and architecture foundation. It defines how future work is proposed, approved, implemented, tested, verified, documented, committed, and pushed.

It creates documentation only. It does not implement an application capability.

## 2. Why this step exists

Credit decision systems combine data, models, policy, explanations, regulation, and human judgment. Without explicit responsibility boundaries, a later AI feature could accidentally become a source of invented facts or nondeterministic decisions.

The foundation makes safety, provenance, learning, and evidence requirements explicit before code creates momentum around an unclear design.

## 3. What existed before

The repository contained one tracked file: the final approved `docs/plans/stage-0-plan.md`. The plan was committed and pushed as commit `675c949` before implementation began.

There was no `AGENTS.md`, README, ignore policy, current architecture, roadmap, workflow, documentation standard, learning standard, zero-cost policy, explainer, or stage summary.

## 4. What exists afterward

The repository has:

- a command-oriented working agreement for future Codex sessions;
- a human-facing project orientation;
- an authoritative architecture with decision statuses;
- a nine-stage roadmap with two sacred gates;
- development and documentation lifecycles;
- interview-learning and zero-cost standards;
- repository hygiene rules;
- a traceable explanation of this implementation.

Application functionality remains unimplemented.

## 5. Files created or modified

Created during the governance-foundation implementation:

- `AGENTS.md`
- `README.md`
- `.gitignore`
- `docs/architecture.md`
- `docs/project-roadmap.md`
- `docs/development-workflow.md`
- `docs/documentation-standard.md`
- `docs/interview-learning-standard.md`
- `docs/zero-cost-constraints.md`
- `docs/explanations/stage-0/step-0-project-foundation.md`

The approved plan was inspected but not modified.

The retrospective `docs/explanations/stage-0/stage-0-summary.md` is created only after candidate verification runs.

## 6. Architecture and data-flow walkthrough

The planned system moves from verified data through deterministic validation, features, model scoring, calibration, explainability, policy evaluation, scenarios, services, and audit before grounded AI assistance reaches a human reviewer.

The governance documents surround that technical flow. The approved plan preserves intended scope. Architecture records current responsibility boundaries. The roadmap controls dependency order. Specialized standards govern workflow, documentation, learning, and cost. Explainers and summaries preserve actual evidence.

## 7. Important implementation explained

`AGENTS.md` permits a minimal read-only Git preflight before it is read. After that, it requires itself and the authoritative project documents to be read before substantive judgments, proposals, or changes.

`docs/architecture.md` separates locked principles, provisional decisions, and open decisions. This prevents an early recommendation from being mistaken for an immutable fact or an unresolved choice from being silently implemented.

Policy execution and retrieval use separate paths. Encoded code produces rule results and reason codes; retrieval supplies passages and citations. The LLM can explain those outputs but cannot interpret prose to execute policy.

`.gitignore` excludes generated payloads while preserving documentation, configuration examples, manifests, lockfiles, schemas, and source code. Local LLM rules address repository-local paths only and do not manage global machine caches.

## 8. New concepts introduced

- **Architecture authority:** the document that says what is currently true about the system design.
- **Historical intent:** what an approved plan said would be built before implementation began.
- **Provenance:** evidence of where data, policy, or claims came from and how they changed.
- **Sacred gate:** a non-negotiable evidence boundary that blocks dependent trust or completion.
- **Abstention:** explicitly saying evidence is insufficient instead of guessing.
- **Deterministic execution:** the same approved inputs and rules produce the same result.

## 9. Design decisions

- Use one authoritative document per governance subject.
- Keep `AGENTS.md` imperative and link to detailed standards.
- Keep the README descriptive and honest about current capability.
- Preserve approved plans rather than rewriting them after execution.
- Put current architecture in `docs/architecture.md` and actual stage outcomes in summaries.
- Use nine capability-level stages rather than fourteen component-sized stages.
- Define sacred gates now but defer exact thresholds to their approved future plans.
- Ignore generated artifacts through explicit project-local paths where ambiguity could hide source.

## 10. Why this approach

Separating responsibilities makes each document easier to maintain and reduces contradictions. A future session can start with concise governing instructions, then follow links to increasingly detailed evidence.

The approach also mirrors good system architecture: each artifact has a clear contract instead of every document trying to contain the whole project.

## 11. Alternatives considered

- Put all governance in one large README.
- Duplicate every important rule in every document.
- Use a separate decision log for each small choice.
- Save raw planning conversations and intermediate drafts.
- Allow plans to be updated in place after implementation changes.
- Ignore entire generic directories such as `models/` or `data/`.

## 12. Why alternatives were rejected or deferred

A single README becomes difficult to navigate and mixes human orientation with enforceable process. Duplication creates drift. Numerous small decision logs add noise at this project stage. Raw conversations are not curated project truth. Rewriting plans destroys historical evidence. Broad ignore patterns can hide reproducibility-critical source or metadata.

Separate architecture decision records may become useful if the decision set grows; for now, the architecture document's structured decision sections are sufficient.

## 13. Tests written

No application tests were written because Stage 0 contains no application.

The step uses repeatable structural and content checks for file scope, required language, headings, decision boundaries, plan immutability, whitespace, and `.gitignore` behavior.

## 14. What the tests prove

The completed preliminary checks prove that:

- the approved plan's Git blob is unchanged;
- exactly the plan plus nine core governance files existed before this explainer;
- the core principle appears in the intended entry-point documents;
- the roadmap contains stages 0 through 8;
- both sacred gates are defined;
- the preflight clarification and global-cache boundary are documented;
- representative sensitive and generated paths are ignored;
- representative reproducibility files remain trackable;
- the checked files have no trailing whitespace.

## 15. What the tests do not prove

Documentation checks do not prove that future code will obey the architecture, that a model will be accurate or calibrated, that retrieval will be grounded, that policy rules will be correct, or that the final product will be fair, secure, compliant, or production-ready.

Those claims require later implementation and approved stage-specific evidence.

## 16. Verification results

The preliminary core-document check passed. It checked the approved-plan blob, ten-file inventory, required principles, nine roadmap stages, both sacred gates, preflight ordering, project-local cache boundary, current-versus-planned README language, plan-preservation language, whitespace, and `.gitignore` positive and negative cases.

The candidate Stage 0 gate passed after this explainer was created. It confirmed 11 expected files, an unchanged approved-plan blob, all nine roadmap stages, both sacred gates, all 21 explainer sections, required governance language, clean whitespace and EOF formatting, and the approved `.gitignore` behaviors.

Final post-summary content verification passed. It confirmed the exact 12-file Stage 0 scope, unchanged approved plan, authority and governance content, roadmap and sacred gates, explainer and summary structure, honest capability claims, `.gitignore` behavior, and clean formatting.

## 17. Problems encountered

No material architectural contradiction was found during implementation.

The main documentation risk was circular duplication: several files need to mention the same safety principle and workflow without becoming competing sources of truth.

## 18. How problems were solved

Each subject received one authoritative document. Secondary documents contain concise summaries and identify the detailed source. Verification checks repeated terminology and boundaries for consistency.

The summary's retrospective nature is handled through two passes: candidate verification before the summary, then final verification after it records actual results.

## 19. Interview questions and strong answers

### Why create governance before application code?

Because underwriting combines high-risk responsibilities. Establishing data provenance, decision authority, verification gates, and change control first reduces the chance that later components acquire unsafe or ambiguous responsibilities.

### Why can the LLM explain a policy result but not execute policy?

Policy execution must be deterministic, testable, and reproducible. An LLM can cite and summarize the source behind an encoded result, but interpreting prose to decide eligibility would create nondeterministic outcomes and weak audit evidence.

### Why preserve an approved plan after the implementation changes?

The plan is evidence of original intent. Preserving it lets reviewers compare intention with execution, understand approved deviations, and avoid rewriting project history.

## 20. Hard or senior-level interview questions

### How do you prevent governance documents from drifting apart?

Assign one authoritative document per subject, link instead of copying detailed rules, use consistent vocabulary, verify cross-document requirements, and treat disagreement between code and current documentation as a defect.

### Why are gate thresholds deferred?

Stage 0 lacks the source evidence needed to choose meaningful metrics. The relevant stage must define thresholds before seeing final results so the team cannot tune acceptance criteria retroactively.

### Is deterministic policy code automatically correct?

No. Determinism only makes behavior repeatable. Correctness still requires an approved policy source, traceable rule encoding, boundary tests, versioning, and human review.

## 21. What comes next and why

After candidate verification, the project creates the retrospective Stage 0 summary, reruns the full gate, commits, and pushes the governance foundation.

Stage 1 must not begin immediately. Its final plan must first investigate the repository's inherited constraints, propose how to establish domain and data meaning, receive approval, and be committed and pushed.
