# System Architecture

## Purpose and authority

This document is the authoritative source for the platform's current architectural boundaries and significant technical decisions. The roadmap controls when capabilities are built; approved stage plans preserve original stage intent; explainers and summaries record actual execution.

If an approved deviation changes current architecture, preserve the original plan and update this document after approval.

## Decision statuses

- **Locked principle:** a foundational safety or responsibility boundary that cannot change without explicit architectural approval.
- **Provisional decision:** the current recommended direction, subject to evidence from the relevant stage.
- **Open decision:** intentionally unresolved; implementation must not fill it through assumption.

Every significant decision records its choice, rationale, realistic alternatives, deferral reasoning, and revisit conditions.

## Product context and limitations

The provisional product context is unsecured personal lending. This creates a coherent demonstration domain without claiming a specific lender, jurisdiction, or customer population.

The Home Credit dataset must not be described as representative of U.S. bank customers, a particular lender, current lending conditions, or a production population. The meaning and prediction horizon of its `TARGET` field are open until Stage 1 examines authoritative source documentation. Until then, retain the source name `TARGET` and do not call it default.

The platform is educational. It is not legally certified, regulator-approved, production-ready, or suitable for real lending decisions.

## Locked responsibility boundary

> **LLM explains; deterministic systems decide.**

Applicant facts come from verified application or database data. Risk values come from an approved model pipeline. Risk explanations come from the explainability layer. Policy outcomes come from deterministic encoded rules. Scenario values come from a constrained deterministic engine. Policy and regulatory explanations are grounded in retrieved sources. A human retains final decision authority.

The LLM must not independently calculate risk or financial values, execute policy by interpreting prose, invent facts or requirements, approve or decline an applicant, or override deterministic or human outputs. Missing evidence requires explicit abstention.

Alternatives rejected:

- LLM-first underwriting is flexible but cannot provide the determinism, reproducibility, traceability, or decision authority this project requires.
- Allowing the LLM to recompute numeric results creates multiple sources of truth and makes audit evidence unreliable.

Revisit condition: none within the current project purpose. A change would redefine the project and requires explicit architectural approval.

## Provenance categories

These categories remain logically and visibly separate:

1. Historical Home Credit source data.
2. Engineered model features derived deterministically from source data.
3. Synthetic demonstration identities and workflow fields.
4. Fictional internal lending policy.
5. Authoritative real regulatory material.

Their provenance must remain traceable through storage, services, audit records, explanations, and UI labels. Synthetic fields must not silently enter model training or evaluation. Fictional policy must not be presented as law, and regulatory sources must not be presented as internal policy.

## Planned component flow

```text
historical or verified application data
  → validation
  → feature engineering
  → credit-risk model
  → probability calibration
  → explainability
  → deterministic policy engine
  → constrained scenario engine
  → service, persistence, and audit layer
  → grounded AI assistance
  → human review and decision
```

This flow describes intended boundaries, not currently implemented functionality. Each component must expose explicit inputs, outputs, versions, and provenance. A downstream component may consume an approved upstream output but may not silently recreate its responsibility.

## Policy execution and retrieval

Policy has two separate paths.

Deterministic execution:

```text
versioned fictional policy source
  → reviewed encoded rule
  → deterministic evaluation
  → triggered/not triggered
  → rule ID and reason code
```

Knowledge retrieval:

```text
versioned policy or authoritative regulatory source
  → provenance-aware index
  → retrieved passage
  → grounded explanation and citation
```

Retrieval explains an already-computed rule result or answers a supported knowledge question. It never substitutes for executable policy. If prose has not been encoded as a deterministic rule, the system reports that no executable policy determination is available.

Both paths should share policy version, rule identifier, document identifier, source section, and effective-date metadata where applicable. Later consistency tests must detect drift.

Alternative rejected: asking an LLM to interpret policy directly is easier to prototype but creates nondeterministic decisions and weak auditability.

## Human authority

The planned interface supports a human reviewer; it does not replace one. Model risk, policy results, scenario outputs, and LLM explanations are evidence for review. The LLM cannot commit or override the final human decision. Audit records must distinguish system outputs from human actions.

## Cross-cutting qualities

Every relevant stage must address:

- correctness and explicit contracts;
- provenance and versioning;
- reproducibility;
- auditability;
- security and privacy;
- tests proportional to risk;
- honest limitation reporting;
- responsible-AI and fair-lending analysis where supported.

Fair-lending analysis must distinguish evaluation attributes from model inputs and must not claim proof of fairness, compliance, or legal certification. Regulatory statements require authoritative public sources and would require qualified professional review before real-world use.

## Sacred gates

### Sacred Gate 1 — Credit Model Integrity

Nothing downstream may rely on the model as a trustworthy risk source until approved evidence addresses target semantics, leakage controls, train/validation/test isolation, deterministic preprocessing, reproducibility, predictive evaluation, probability calibration, stability, supported subgroup analysis, and limitations.

Exact metrics and thresholds are open until approved before Stage 3 evaluation. They must not be chosen retroactively.

### Sacred Gate 2 — Grounding & Decision Authority

The AI-assisted product is incomplete until evaluation shows no fabricated applicant facts or policy/regulatory claims, correct abstention, fidelity to deterministic outputs, evidence-backed citations, no independent deterministic calculations or policy interpretation, and no override of model, policy, scenario, or human authority.

The Stage 7 plan must approve the evaluation harness and thresholds before execution. The gate is repeated during final integration.

## Technology decisions

### FastAPI backend boundary

- Status: locked for the current architecture, revisitable only through an approved change.
- Choice: use FastAPI as the initial service boundary.
- Why: typed contracts, Python-native ML integration, automatic API documentation, dependency injection, and testability.
- Alternatives: Flask offers less structure by default; Django adds broader framework machinery than the initial API-focused need.
- Revisit when: evidence shows FastAPI cannot meet an approved service, security, or deployment requirement.

### SQLite persistence

- Status: provisional.
- Choice: begin with SQLite for the local single-user demonstration.
- Why: free, portable, low-setup, and compatible with local-first development.
- Alternative: PostgreSQL provides stronger concurrency and operational capabilities at greater setup cost.
- Revisit when: concurrency, migration, audit, or deployment requirements justify PostgreSQL.

### React, TypeScript, and Vite frontend

- Status: provisional.
- Choice: use React with TypeScript and Vite for the planned reviewer UI.
- Why: recognizable component model, stronger interfaces, lightweight tooling, and no current server-side-rendering need.
- Alternative: Next.js adds server-side and full-stack conventions that are not presently required.
- Revisit when: server-side rendering, framework routing, or deployment requirements materially change.

### Local ML and AI stack

- Status: provisional direction with open implementation choices.
- Direction: Python, scikit-learn baseline, a justified LightGBM or XGBoost candidate, SHAP, local MLflow, Ollama, sentence-transformers, FAISS, and later Docker packaging.
- Why: supports a zero-cost local core and the required deterministic boundaries.
- Alternatives: managed model, vector, experiment, or database services can reduce operations but create cost and external dependencies.
- Revisit when: a future stage establishes requirements and compares evidence. Paid services cannot become required core dependencies.

## Open decisions

Open items include `TARGET` meaning and horizon, precise decision states, jurisdiction and regulatory sources, acquisition mechanics, split methodology, features, final model family, gate thresholds, responsible-AI metrics, sensitive-attribute treatment, final persistence needs, audit tamper evidence, authentication, local LLM and embedding choices, retrieval thresholds, and deployment target, hosted-demo, and optional-integration choices.

Open decisions must be resolved in approved stage plans rather than through undocumented assumptions.
