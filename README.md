# AI-Powered Credit Underwriting & Decision Intelligence Platform

An educational, portfolio-grade project exploring how deterministic credit-risk, policy, explainability, retrieval, and audit components can support a human underwriting workflow.

## Current status

The repository currently contains the Stage 0 governance and architecture foundation. It does not yet contain application code, a data pipeline, a trained model, policy rules, an API, a copilot, or a user interface.

Stage 1 implementation has not begun. Its plan must be reviewed, approved, committed, and pushed before work starts.

## Governing principle

> **LLM explains; deterministic systems decide.**

The planned LLM will explain verified outputs and retrieved evidence. It will not independently calculate risk, execute lending policy, approve or decline applicants, invent facts, or override deterministic components or human authority.

## Provisional scope

The provisional product context is unsecured personal lending. The historical Home Credit dataset is planned as the primary ML source, but it must not be presented as representative of U.S. bank customers, a particular lender, or a production population.

The exact meaning and prediction horizon of Home Credit's `TARGET` field remain unresolved until authoritative source documentation is examined during Stage 1.

## Planned architecture

The planned flow is:

```text
verified data
  → validation and feature engineering
  → risk model and calibration
  → model explainability
  → deterministic policy and scenario engines
  → FastAPI services, persistence, and audit
  → grounded AI assistance
  → human review and decision
```

This is a roadmap, not a claim that these capabilities currently exist.

FastAPI is the accepted initial backend boundary. SQLite is the provisional initial persistence choice. React, TypeScript, and Vite are the provisional frontend choice. Later stages must validate implementation-specific choices before relying on them.

## Data and knowledge boundaries

The project will keep historical source data, engineered features, synthetic demo identities, fictional internal policy, and authoritative real regulatory material distinct and traceable.

Policy rules will be executed by deterministic code. Retrieval will supply source passages and citations for explanations; an LLM will not execute policy by interpreting prose.

## Project stages

- Stage 0 — Governance & Architecture
- Stage 1 — Credit Domain & Data Foundation
- Stage 2 — Analytical Dataset & Feature Engineering
- Stage 3 — Credit Risk Modeling
- Stage 4 — Explainability & Decision Intelligence
- Stage 5 — Policy, Regulatory Knowledge & Grounding
- Stage 6 — Application Services, Persistence & Audit
- Stage 7 — AI-Assisted Human Underwriting
- Stage 8 — Integrated Governance, Evaluation & Portfolio Release

See `docs/project-roadmap.md` for dependencies and gates.

## Documentation map

- `AGENTS.md` — governing instructions for Codex sessions
- `docs/architecture.md` — current architectural source of truth
- `docs/project-roadmap.md` — capability stages and verification gates
- `docs/plans/` — final approved stage plans and preserved original intent
- `docs/explanations/` — implementation explainers and stage summaries
- `docs/development-workflow.md` — approval-through-push lifecycle
- `docs/documentation-standard.md` — documentation requirements
- `docs/interview-learning-standard.md` — teaching and interview standards
- `docs/zero-cost-constraints.md` — `$0` core rules

## Safety and limitations

This project is for education and demonstration. It is not legally certified, regulator-approved, production-ready, or suitable for real lending decisions. Responsible-AI and fair-lending analysis will document evidence and limitations without claiming proof of fairness or compliance.
