# Stage 0 Plan — Governance & Architecture

## 1. Context entering the stage

The project is an **AI-Powered Credit Underwriting & Decision Intelligence Platform** intended to be portfolio-grade, educational, and suitable for interview preparation.

The repository was last observed in this state:

- Git initialized locally.
- Current branch: `main`.
- No commits.
- No application or project files.
- `origin` configured as:
  `https://github.com/RushilJoshi07/ai-credit-underwriting.git`
- Remote repository history and push authentication not yet verified.

Before creating the first commit, the local state and remote refs must be reinspected. If the GitHub repository contains an independent history, implementation must stop until a safe integration approach is approved.

## 2. Stage objective

Stage 0 will establish the project’s authoritative:

- working agreement;
- architectural boundaries;
- high-level roadmap;
- development workflow;
- verification philosophy;
- documentation and interview-learning standards;
- zero-cost constraints;
- approved-plan preservation process.

Stage 0 will not build any application capability. Its purpose is to make future development deliberate, explainable, reproducible, and auditable.

## 3. Core engineering principle

The project’s central boundary is:

> **LLM explains; deterministic systems decide.**

The LLM must never independently:

- calculate probability of default or any equivalent risk value;
- perform financial calculations assigned to deterministic components;
- approve, decline, or otherwise determine a lending outcome;
- infer that a policy rule is satisfied by interpreting policy prose;
- invent applicant facts;
- invent lending-policy requirements;
- invent regulatory requirements;
- override model, policy-engine, scenario-engine, or human outputs;
- present unsupported information as established fact.

Applicant facts must come from verified application or database records.

Risk values must come from approved deterministic model pipelines.

Risk explanations must come from the approved explainability layer.

Policy results must come from deterministic, tested rules.

Policy and regulatory explanations must be grounded in retrieved, versioned source material.

Unsupported questions must receive an explicit insufficient-evidence response.

The final lending decision remains a human responsibility in the demo workflow. This project must not claim autonomous underwriting authority.

## 4. Provisional product scope

The provisional product is:

> **Unsecured personal lending**

This scope provides a coherent planning context without asserting that the eventual system represents any specific lender, jurisdiction, or customer population.

The project must not claim that the Home Credit dataset represents:

- U.S. bank customers;
- the customers of a specific lender;
- the intended deployment population;
- current lending conditions;
- a production-ready underwriting population.

The scope may be revisited only through the approved architectural-change process.

## 5. Data and knowledge provenance boundaries

The system must preserve a strict distinction between:

1. **Historical source data**
   Original Home Credit tables and their documented fields.

2. **Engineered model features**
   Deterministically derived values created from historical source data.

3. **Synthetic demonstration data**
   Fictional identities or workflow fields created only to make the product demonstration realistic.

4. **Fictional internal lending policy**
   Demo-lender policy created for the project and always labeled as fictional.

5. **Authoritative regulatory material**
   Real public material obtained from authoritative regulatory or governmental sources.

These categories must not be blended or presented under ambiguous labels. Their provenance must remain visible in storage, APIs, audit records, explanations, and the user interface.

Synthetic identity or workflow data must not silently enter model training or evaluation.

Fictional policy must not be represented as law.

Regulatory material must not be represented as fictional internal policy.

## 6. Home Credit target semantics

The exact meaning of Home Credit’s `TARGET` field and the prediction horizon remain unresolved until authoritative source documentation is inspected during Stage 1.

Until then:

- retain the source name `TARGET`;
- do not casually rename it to `default`;
- do not assert a prediction horizon;
- do not imply that it matches a particular legal or business definition of default;
- do not design model claims that depend on an unverified interpretation.

Stage 1 must document the source definition, its limitations, and the terminology the project may safely use afterward.

## 7. System responsibility boundaries

The intended high-level flow is:

```text
Historical or verified application data
  → validation
  → feature engineering
  → credit-risk model
  → probability calibration
  → explainability
  → deterministic policy engine
  → constrained scenario engine
  → service and audit layer
  → grounded underwriting copilot
  → human review and decision
```

Cross-cutting responsibilities include:

- provenance;
- versioning;
- reproducibility;
- testing;
- security;
- auditability;
- responsible-AI evaluation;
- clear limitation reporting.

Each component must expose explicit inputs and outputs. Later components may consume approved upstream outputs but must not silently recreate upstream responsibilities.

## 8. Deterministic policy execution and policy retrieval

Policy execution and policy retrieval are separate architectural paths.

### Deterministic policy execution

```text
Versioned policy source
  → reviewed encoded rule
  → deterministic evaluation
  → triggered/not triggered
  → rule ID and reason code
```

Code determines whether the applicant satisfies or violates an executable policy rule.

Rules must be versioned, tested, and traceable to their fictional policy source.

### Policy RAG and knowledge retrieval

```text
Versioned policy source
  → document processing and retrieval index
  → relevant source passage
  → grounded explanation and citation
```

Retrieval supplies evidence for explaining a rule or answering a supported policy question.

The runtime LLM must not retrieve English policy text and independently decide whether the applicant satisfies that policy.

If a policy requirement exists only as prose and has not been encoded into the deterministic engine, the system must report that no executable policy determination is available.

The rule engine and retrieval system should share provenance metadata such as:

- policy version;
- rule identifier;
- source section;
- effective date;
- document identifier.

Consistency tests must detect drift between executable rules and explanatory source material.

## 9. Provisional technology direction

### Backend boundary: FastAPI

FastAPI is the initial backend boundary because it supports:

- explicit request and response contracts;
- Python-native integration with ML and policy components;
- automatic API documentation;
- dependency injection and testability;
- clear separation between domain logic and transport logic.

Realistic alternatives include Flask and Django.

- Flask is flexible but provides fewer conventions and less contract support by default.
- Django offers a comprehensive application framework but introduces more machinery than the initial API-focused architecture requires.

FastAPI may be revisited through the architectural-change process if later evidence exposes a material limitation.

### Persistence: SQLite, provisionally

SQLite is the initial provisional persistence choice because it is:

- free;
- local;
- simple to configure;
- portable;
- sufficient for a single-user portfolio demonstration;
- compatible with a local-first workflow.

PostgreSQL is the principal realistic alternative. It provides stronger concurrency and operational features but requires additional setup and infrastructure.

The persistence design should avoid unnecessary SQLite-specific coupling so PostgreSQL can be adopted later if concurrency, audit, migration, or deployment requirements justify it.

### Frontend: React, TypeScript, and Vite, provisionally

React with TypeScript and Vite is the provisional frontend choice because:

- React is widely recognizable in interviews;
- TypeScript strengthens interface correctness;
- Vite provides a lightweight development and build workflow;
- FastAPI already owns the backend boundary;
- the current product does not require server-side rendering or search-engine optimization.

Next.js is the principal realistic alternative. It should be reconsidered if server-side rendering, full-stack framework conventions, framework routing, or deployment requirements become important.

### ML and AI tooling

The current direction includes:

- Python;
- scikit-learn for an interpretable baseline;
- LightGBM or XGBoost as later candidates;
- SHAP;
- local MLflow tracking;
- Ollama and an open-source local LLM;
- sentence-transformers;
- FAISS;
- Docker when packaging becomes useful.

The final boosted-tree library, local LLM, embedding model, and detailed tooling choices remain open until their stages establish requirements and compare realistic alternatives.

## 10. Zero-cost core operation

The complete core project must be buildable and runnable for `$0`.

A required core workflow must not depend on:

- a paid API;
- a paid database;
- paid model inference;
- a paid vector database;
- a paid monitoring platform;
- a paid hosted deployment;
- a free trial that later requires payment;
- a proprietary service with no local alternative.

Free-tier hosted services may be optional conveniences, but the core must retain a documented local path.

GitHub and GitHub Actions may be used where free usage is sufficient. Essential verification must also be runnable locally so exhaustion or removal of hosted free-tier capacity does not make the project unusable.

Any proposed dependency that may incur cost requires explanation and approval before becoming part of the required architecture.

## 11. Responsible AI and fair-lending posture

Responsible-AI and fair-lending analysis are mandatory governance concerns, but the project must not claim:

- legal certification;
- regulatory approval;
- production lending suitability;
- proof of fairness;
- elimination of discrimination;
- causal validity from observational model explanations;
- professional legal or compliance advice.

Later stages should assess, where the data and context support it:

- subgroup performance;
- subgroup calibration;
- error-rate differences;
- proxy and leakage risks;
- representativeness limitations;
- explainability limitations;
- data-quality limitations;
- human-review risks;
- automation-bias risks.

Evaluation data used for responsible-AI analysis must be distinguished from features allowed to influence a lending model.

Applicable jurisdictions, protected-class analysis, regulatory interpretations, metrics, and acceptable thresholds remain open until the domain and data are understood. Authoritative sources and qualified professional review would be required before any real-world use.

## 12. High-level project stages

The roadmap will use nine major stages.

A stage represents a major product capability that can be explained and defended as a coherent unit.

A step represents an independently implemented, tested, documented, committed, and pushed component within a stage.

This granularity avoids two problems:

- Fourteen narrow stages would make the learning narrative fragmented and treat implementation components as product-level milestones.
- Fewer, very broad stages would obscure dependencies and create gates too large to verify meaningfully.

### Stage 0 — Governance & Architecture

Establish working rules, architecture, roadmap, documentation standards, plan persistence, and verification gates.

### Stage 1 — Credit Domain & Data Foundation

Representative steps:

- define provisional product terminology;
- inspect authoritative Home Credit documentation;
- resolve or accurately constrain `TARGET` semantics;
- document licensing and provenance;
- acquire data reproducibly;
- catalog tables and relationships;
- validate raw data;
- formalize separation of historical and synthetic data.

### Stage 2 — Analytical Dataset & Feature Engineering

Representative steps:

- define split strategy;
- establish leakage controls;
- design cleaning and missingness rules;
- aggregate relational tables;
- build reproducible borrower-level features;
- validate schemas and deterministic output.

### Stage 3 — Credit Risk Modeling

Representative steps:

- establish an interpretable baseline;
- compare justified candidate models;
- evaluate predictive performance;
- evaluate and improve probability calibration;
- test stability and reproducibility;
- track experiments;
- document model limitations.

This stage ends at Sacred Gate 1.

### Stage 4 — Explainability & Decision Intelligence

Representative steps:

- implement SHAP-based analysis;
- distinguish global and local explanations;
- validate explanation fidelity;
- create model reason abstractions;
- document non-causal limitations;
- build constrained scenario and counterfactual analysis;
- prevent infeasible or misleading recommendations.

### Stage 5 — Policy, Regulatory Knowledge & Grounding

Representative steps:

- author and version fictional internal policy;
- implement deterministic rules and reason codes;
- test policy boundaries;
- identify authoritative regulatory sources;
- create provenance-aware document ingestion;
- implement retrieval and citations;
- test insufficient-evidence behavior;
- detect drift between rule execution and policy explanation sources.

### Stage 6 — Application Services, Persistence & Audit

Representative steps:

- define domain-service contracts;
- expose deterministic capabilities through FastAPI;
- implement provisional SQLite persistence;
- preserve application, model, feature, policy, and source versions;
- create an auditable event trail;
- establish authorization and data-handling boundaries;
- test reconstruction of a decision record.

This stage precedes the copilot so the LLM consumes stable, tested interfaces rather than ad hoc logic.

### Stage 7 — AI-Assisted Human Underwriting

Representative steps:

- define typed copilot tools;
- connect only to approved deterministic services;
- implement grounded generation and citation behavior;
- implement explicit abstention;
- test prohibited behavior;
- build the React/TypeScript/Vite reviewer interface;
- preserve human decision authority;
- test the complete reviewer workflow.

This stage ends at Sacred Gate 2.

### Stage 8 — Integrated Governance, Evaluation & Portfolio Release

Representative steps:

- run integrated acceptance and responsible-AI evaluation;
- complete security and privacy review;
- establish CI within zero-cost constraints;
- package the application reproducibly;
- verify clean-environment setup;
- complete portfolio and interview documentation;
- produce an honest readiness and limitation assessment.

Governance is enforced throughout all stages. Stage 8 consolidates its evidence rather than introducing governance for the first time.

## 13. Sacred verification gates

Sacred gates are non-negotiable release boundaries. A dependent capability may not be described as trusted or complete until its sacred gate passes.

### Sacred Gate 1 — Credit Model Integrity

Nothing downstream may rely on the credit model as a trustworthy source of risk values until evidence covers at least:

- documented target semantics and provenance;
- target and feature leakage controls;
- train/validation/test isolation;
- deterministic preprocessing;
- reproducibility;
- appropriate predictive evaluation;
- probability evaluation and calibration;
- stability analysis;
- subgroup analysis where supported;
- explicit limitations.

Step 0 establishes these required categories, not their final numerical thresholds.

Metrics, tolerances, and failure rules must be proposed and approved before the gate is evaluated. They must not be selected retroactively to make a model appear successful.

Independent development may continue, but no downstream component may present an unapproved model output as trusted.

### Sacred Gate 2 — Grounding & Decision Authority

The AI-assisted product cannot be considered complete until an evaluation harness demonstrates that it:

- does not fabricate applicant facts;
- does not fabricate policy or regulatory claims;
- abstains when evidence is missing or insufficient;
- does not independently calculate model, policy, eligibility, or financial results;
- accurately reflects approved deterministic outputs;
- supplies traceable evidence and citations;
- distinguishes fictional policy from real regulatory material;
- does not execute lending policy through LLM interpretation;
- cannot override the model, policy engine, scenario engine, or human reviewer;
- does not represent itself as the final decision-maker.

Exact cases, coverage requirements, thresholds, and failure behavior must be approved before this gate is run.

Sacred Gate 2 is evaluated during Stage 7 and repeated during the final integrated release assessment.

## 14. Development workflow

Every non-trivial logical step follows:

> **Explain → approve → implement → test → verify → explain → document → commit → push**

### Explain

Before implementation:

- inspect the relevant repository state;
- explain what is proposed;
- introduce unfamiliar concepts;
- explain why the approach fits;
- present realistic alternatives;
- state tradeoffs and expected files;
- identify verification and rollback considerations.

### Approve

Wait for explicit approval before non-trivial implementation.

Approval applies to the explained scope. Material expansion or architectural deviation requires a new proposal and approval.

### Implement

Make only the approved changes. Preserve unrelated user work and avoid silently altering settled decisions.

### Test and verify

Run checks proportional to risk. Distinguish:

- what the tests prove;
- what they do not prove;
- automated test results;
- manual or structural verification;
- unresolved limitations.

### Explain and document

Explain the result and update the authoritative documentation before completing the logical step.

### Commit

Each completed logical step receives a focused, descriptive commit. Avoid vague messages such as `updates`, `fixes`, or `work`.

### Push

A completed, verified, documented commit is normally pushed to `origin`.

The first upstream push is expected to use:

```text
git push -u origin main
```

Later completed commits are pushed normally without separate authorization.

Stop and request direction if there is:

- unexpected remote history;
- authentication failure;
- connectivity failure that prevents safe completion;
- a non-fast-forward condition;
- unexpected branch protection;
- remote mismatch;
- another genuine repository or safety concern.

Force-pushing is not part of the normal workflow.

## 15. Approved stage-plan persistence

Every major stage must have one authoritative approved plan:

```text
docs/plans/stage-N-plan.md
```

Before proposing a stage plan, inspect:

- the current repository;
- `AGENTS.md`;
- `docs/architecture.md`;
- `docs/project-roadmap.md`;
- previous approved plans;
- relevant step explainers;
- previous stage summaries;
- existing code and tests.

The planning cycle is:

1. inspect;
2. propose;
3. explain;
4. wait for external review;
5. revise when requested;
6. receive explicit final approval;
7. save only the approved plan;
8. verify, commit, and push the plan;
9. implement the stage through the normal step workflow.

An approved plan should normally record:

- entering context and repository state;
- stage objective;
- inherited dependencies;
- scope;
- out-of-scope and deferred work;
- important decisions;
- alternatives;
- rejection or deferral reasoning;
- step order;
- expected deliverables;
- verification strategy;
- stage gate;
- decisions locked for the stage;
- decisions still open;
- assumptions inherited by the next stage.

Raw conversations, intermediate proposals, external review discussion, and superseded drafts must not be committed.

### Preserving historical intent

Once implementation begins, the original intended decisions must not be silently rewritten to make the plan appear consistent with later execution.

If a material deviation becomes necessary:

1. explain the problem and proposed deviation;
2. present benefits, costs, and alternatives;
3. wait for approval;
4. preserve the original plan text;
5. record the deviation in the relevant step explainer;
6. record it in the final stage summary;
7. when useful, append a clearly labeled approved amendment or deviation section to the stage plan;
8. update `docs/architecture.md` when the current architectural source of truth genuinely changes;
9. verify, commit, and push the approved documentation changes.

Minor implementation details that do not alter scope, architecture, responsibility boundaries, or approved outcomes do not require an amendment.

## 16. Step explainers

Every meaningful completed implementation step must have an explainer under:

```text
docs/explanations/stage-N/
```

Each explainer must contain sections equivalent to:

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

The sections may be adapted to the nature of the step, but substantive requirements must not be silently omitted.

## 17. Stage summaries

After the implementation satisfies its candidate stage gate, create a stage summary documenting:

- stage objective;
- completed steps;
- how the components interact;
- major design decisions;
- approved deviations from the original plan;
- verification gate;
- what was proven;
- what was not proven;
- remaining limitations;
- final test status;
- interview defense;
- final outcome;
- dependencies and assumptions the next stage may safely inherit.

The complete documentation set must then undergo a final verification pass. A stage is not declared complete until its summary is accurate, committed, and pushed.

The plan records intended work. The summary records actual work. Both must remain trustworthy.

## 18. Repository inspection rule

Before reporting project status or proposing work, inspect the repository rather than relying only on conversation history.

A fresh session should be able to reconstruct the project in this order:

```text
AGENTS.md
→ docs/architecture.md
→ docs/project-roadmap.md
→ approved docs/plans/
→ step explainers
→ stage summaries
→ implementation and tests
→ Git history
```

Conversation history is not an authoritative project dependency.

## 19. Correctness and auditability priorities

When priorities conflict, prefer:

1. correctness;
2. transparency;
3. reproducibility;
4. auditability;
5. safety;
6. maintainability;
7. clarity;
8. performance where demonstrated necessary;
9. cleverness last.

No implementation should obscure provenance or responsibility merely to appear sophisticated.

## 20. Stage 0 scope

Stage 0 includes:

- persisting this approved plan;
- creating the governing instructions;
- documenting the architecture and its decision status;
- defining the nine-stage roadmap;
- defining development and GitHub workflow;
- defining documentation and learning standards;
- recording zero-cost constraints;
- creating repository hygiene exclusions;
- creating the Stage 0 explainer and summary;
- verifying, committing, and pushing the completed foundation.

## 21. Stage 0 out of scope

Stage 0 will not create or implement:

- application source code;
- test code for a future application;
- dependency manifests;
- virtual environments;
- frontend scaffolding;
- API scaffolding;
- databases or schemas;
- downloaded datasets;
- data-acquisition scripts;
- model code or artifacts;
- policy rules or policy documents;
- regulatory corpora;
- embeddings or vector indexes;
- CI workflows;
- Docker files;
- hosted deployments;
- exact `TARGET` semantics;
- a prediction horizon;
- numerical model thresholds;
- final fairness metrics;
- final jurisdictional conclusions.

## 22. Step 0 files

### Approved plan artifact

```text
docs/plans/stage-0-plan.md
```

This file must be committed and pushed before the rest of Stage 0 is implemented.

### Governance and architecture implementation

```text
AGENTS.md
README.md
.gitignore
docs/architecture.md
docs/project-roadmap.md
docs/development-workflow.md
docs/documentation-standard.md
docs/interview-learning-standard.md
docs/zero-cost-constraints.md
docs/explanations/stage-0/step-0-project-foundation.md
docs/explanations/stage-0/stage-0-summary.md
```

No other project files are expected during Stage 0.

## 23. Artifact responsibilities

### `AGENTS.md`

The governing instruction document for Codex. It will enforce teaching behavior, approval boundaries, repository inspection, stage gates, testing, documentation, commits, pushes, plan preservation, zero-cost operation, and deterministic-versus-generative boundaries.

### `README.md`

The human entry point. It will explain the project purpose, central principle, provisional scope, high-level architecture, current status, safety disclaimer, and documentation map without pretending unimplemented capabilities exist.

### `.gitignore`

Repository hygiene for Python, frontend, editors, secrets, local databases, downloaded data, model artifacts, MLflow output, logs, caches, and generated files. It will avoid excluding source, reproducibility metadata, approved documentation, and deliberately small fixtures.

### `docs/architecture.md`

The authoritative current architectural source of truth. Significant decisions will record:

- choice;
- status;
- rationale;
- alternatives;
- rejection or deferral reasoning;
- revisit conditions.

It will distinguish accepted principles, provisional technology choices, and open decisions.

### `docs/project-roadmap.md`

The nine-stage capability roadmap, including dependencies, representative steps, deliverables, stage gates, and both sacred gates.

### `docs/development-workflow.md`

The complete explain-through-push cycle, approval boundaries, remote-safety behavior, deviation handling, and commit discipline.

### `docs/documentation-standard.md`

The approved-plan, step-explainer, stage-summary, authoritative-document, and historical-preservation requirements.

### `docs/interview-learning-standard.md`

A standard for beginner-friendly concept teaching, design reasoning, likely interview questions, strong answers, senior follow-ups, limitations, and avoidance of rote memorization.

### `docs/zero-cost-constraints.md`

The `$0` core requirement, acceptable local dependencies, optional-service rules, free-tier risks, and approval requirements for possible costs.

### Step 0 explainer and summary

The explainer will describe how the foundation was implemented.

The summary will compare the result with this plan, record verification evidence, identify approved deviations, state limitations, and define what Stage 1 planning may safely assume.

## 24. Step 0 verification gate

Stage 0 passes only when all of the following are true:

### Repository and remote

- Local repository state has been reinspected.
- `origin` is the intended GitHub repository.
- Remote history was checked before the first commit.
- No unexpected independent history was overwritten.
- The approved plan commit exists locally and remotely.
- The completed Stage 0 commit exists locally and remotely.
- Local `main` and remote `main` point to the expected final commit.
- The working tree is clean after completion.

### Scope

- Every expected Stage 0 file exists.
- No unexpected project file was added.
- No application code, dependency manifest, data, model artifact, database, CI configuration, or generated runtime artifact was introduced.
- No secret or credential was committed.

### Governance coverage

- `AGENTS.md` contains every approved behavior and responsibility boundary.
- The normal workflow ends with commit and push.
- Approved plans are preserved before implementation.
- Material deviations require explanation and approval.
- Original approved intent cannot be silently rewritten.
- Repository inspection is required before status determinations.

### Architecture coverage

- The unsecured-personal-lending scope is labeled provisional.
- Home Credit population limitations are explicit.
- `TARGET` meaning and horizon remain unresolved.
- All five provenance categories are distinguished.
- The LLM/deterministic boundary is explicit.
- Policy execution and policy retrieval are separate.
- Human decision authority is explicit.
- FastAPI is the backend boundary.
- SQLite and React/TypeScript/Vite are labeled provisional.
- Zero-cost operation is a core constraint.
- Responsible-AI and fair-lending analysis is required without claims of certification or production suitability.
- Sacred Gates 1 and 2 are defined.
- Significant choices include rationale, alternatives, and revisit conditions.

### Roadmap and process coverage

- The roadmap uses the approved nine-stage structure.
- Each stage has a coherent capability, dependencies, representative steps, and an exit condition.
- Stage-plan persistence is part of the lifecycle.
- Step explainers contain all required topics.
- Stage summaries distinguish intended from actual work.
- Future sessions can reconstruct project history without conversation access.

### Document quality

- Internal links and referenced paths are valid.
- Markdown structure is readable and consistent.
- Terminology is consistent across files.
- Documents do not claim unimplemented functionality exists.
- Documents do not contradict one another.
- `git diff --check` reports no whitespace errors.
- The final diff contains only intended files.

Because Stage 0 contains no application, no application tests are appropriate. Verification consists of structural, content-coverage, consistency, link, scope, Git, and remote checks.

## 25. Exact implementation sequence after final approval

### Phase A — Preflight

1. Reinspect the working tree, branch, commit history, files, and remote configuration.
2. Run a read-only check of GitHub refs and default-branch state.
3. Confirm that the remote does not contain an independent history.
4. Stop and request direction if the remote state, authentication, branch state, or repository contents are unexpected.

### Phase B — Persist the approved plan

5. Create only `docs/plans/stage-0-plan.md`.
6. Save only this final approved plan—not conversation history or earlier drafts.
7. Verify its completeness, Markdown structure, file scope, and historical-intent rules.
8. Run `git diff --check`.
9. Review the staged-file list and confirm that only the plan is included.
10. Commit:
   `docs(plan): record approved stage 0 plan`
11. Push with upstream tracking:
   `git push -u origin main`
12. Verify that local and remote `main` contain the same plan commit.

### Phase C — Implement the governance foundation

13. Reinspect the committed plan as the authoritative implementation input.
14. Explain that the approved governance-document implementation is beginning.
15. Create:
    - `AGENTS.md`
    - `README.md`
    - `.gitignore`
    - `docs/architecture.md`
    - `docs/project-roadmap.md`
    - `docs/development-workflow.md`
    - `docs/documentation-standard.md`
    - `docs/interview-learning-standard.md`
    - `docs/zero-cost-constraints.md`
16. Cross-check the files against the approved plan and one another.
17. Create `docs/explanations/stage-0/step-0-project-foundation.md`.
18. Run the candidate Step 0 verification gate.
19. Explain the implemented result, tests, limitations, and any problems encountered.
20. If a material deviation is required, stop, propose it, and wait for approval before continuing.
21. Create `docs/explanations/stage-0/stage-0-summary.md` using actual implementation and verification results.
22. Run the full verification gate again, including the explainer and summary.
23. Review the complete diff and staged-file list.
24. Confirm that no out-of-scope files or secrets are present.
25. Commit:
    `docs(project): establish governance and architecture foundation`
26. Push the completed Stage 0 commit to `origin`.
27. Verify that local and remote `main` point to the same commit.
28. Confirm that the working tree is clean.
29. Provide a completion report containing commit identifiers, push status, verification evidence, limitations, and the next proposed activity.

## 26. Decisions locked for Stage 0

The following are locked unless a material issue is explained and a change is approved:

- the nine-stage roadmap structure;
- unsecured personal lending as the provisional planning scope;
- unresolved `TARGET` semantics and prediction horizon;
- separation of the five data and knowledge categories;
- “LLM explains; deterministic systems decide”;
- deterministic policy execution separated from policy retrieval;
- Sacred Gates 1 and 2;
- `$0` core operation;
- FastAPI as the initial backend boundary;
- SQLite as provisional persistence;
- React, TypeScript, and Vite as the provisional frontend;
- human final decision authority;
- responsible-AI analysis without certification claims;
- the explain-through-push workflow;
- approved plan persistence;
- preservation of original plan intent;
- step-explainer and stage-summary requirements;
- normal post-commit pushes to `origin`.

## 27. Decisions intentionally left open

The following remain open for later evidence-based planning:

- authoritative interpretation of `TARGET`;
- prediction horizon;
- precise lending workflow and decision states;
- applicable regulatory jurisdiction and source set;
- data acquisition mechanics and licensing constraints;
- train/validation/test methodology;
- feature definitions;
- final model family;
- model and calibration thresholds;
- responsible-AI metrics and thresholds;
- treatment of protected or sensitive attributes;
- final persistence requirements;
- audit tamper-evidence design;
- authentication and authorization design;
- local LLM and embedding models;
- retrieval evaluation thresholds;
- deployment target;
- optional hosted demonstration approach.

Open decisions must not be filled through undocumented assumptions.

## 28. Dependencies inherited by Stage 1

After Stage 0 passes, Stage 1 may assume:

- project governance is authoritative and available in the repository;
- the architecture distinguishes deterministic and generative responsibilities;
- the provisional product is unsecured personal lending;
- Home Credit semantics still require source investigation;
- provenance categories may not be blended;
- zero-cost and local-first operation are mandatory;
- approved stage plans must be committed and pushed before implementation;
- every completed step requires explanation, approval, testing, verification, documentation, commit, and push;
- Sacred Gate 1 prevents unverified model outputs from becoming trusted dependencies;
- Sacred Gate 2 prevents an ungrounded or decision-making LLM from becoming a completed product;
- Stage 1 itself cannot begin until its own plan is proposed, reviewed, explicitly approved, saved as `docs/plans/stage-1-plan.md`, verified, committed, and pushed.
