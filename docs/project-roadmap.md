# Project Roadmap

## Purpose

This roadmap defines major capabilities, dependency order, expected deliverable categories, and high-level gates. It does not replace an approved stage plan or prematurely settle implementation details.

## Terms

- A **stage** is a coherent product capability that can be explained and defended as one unit.
- A **step** is an independently implemented, tested, documented, committed, and pushed component within a stage.
- A **stage gate** is the evidence required to complete one stage.
- A **sacred gate** is a non-negotiable boundary that blocks dependent trust or product completion.

Nine stages balance learning clarity with technical dependency control. More narrow stages would fragment one capability across artificial milestones; fewer broad stages would make verification too coarse.

Every stage requires a final approved `docs/plans/stage-N-plan.md` committed and pushed before implementation. Exact steps, thresholds, schemas, and tools belong in that plan.

## Stage 0 — Governance & Architecture

- Objective: establish governing rules, architecture, roadmap, documentation standards, plan persistence, and verification gates.
- Depends on: initialized local Git repository and configured GitHub remote.
- Expected deliverables: governance and architecture documents, approved plan, explainer, summary.
- Gate: all approved artifacts exist, agree, make no premature capability claims, pass structural checks, and are committed and pushed.

## Stage 1 — Credit Domain & Data Foundation

- Objective: establish trustworthy product terminology, source meaning, licensing, provenance, and raw data.
- Depends on: Stage 0 governance and approved Stage 1 plan.
- Representative steps: inspect authoritative Home Credit documentation; constrain `TARGET` semantics; document population limits and licensing; acquire data reproducibly; catalog tables and relationships; validate raw data; define historical-versus-synthetic boundaries.
- Expected deliverables: source documentation, acquisition and validation capability, data catalog, provenance records, limitations.
- Gate direction: source meaning and licensing are documented; acquisition is reproducible; raw data integrity checks pass; synthetic content cannot be confused with source data.
- Deferred to the plan: exact sources, commands, schemas, and thresholds.

## Stage 2 — Analytical Dataset & Feature Engineering

- Objective: build a reproducible, leakage-aware modeling dataset.
- Depends on: verified Stage 1 source data and semantics.
- Representative steps: approve split strategy; establish leakage controls; define cleaning and missingness behavior; aggregate relational tables; engineer borrower-level features; validate schemas and determinism.
- Expected deliverables: versioned transformation code, feature definitions, analytical datasets, tests, and limitations.
- Gate direction: deterministic reconstruction, schema validation, split isolation, and leakage review pass.
- Deferred to the plan: split method, features, imputation choices, and quantitative tolerances.

## Stage 3 — Credit Risk Modeling

- Objective: produce and evaluate a calibrated, reproducible risk model.
- Depends on: approved Stage 2 analytical dataset.
- Representative steps: interpretable baseline; justified candidate comparison; predictive and probability evaluation; calibration; stability and subgroup analysis where supported; experiment tracking; model limitations.
- Expected deliverables: trained candidates, evaluation evidence, calibration evidence, model card, reproducible selection record.
- Gate: Sacred Gate 1 — Credit Model Integrity.
- Deferred to the plan: model family, metrics, thresholds, resampling, calibration method, and selection rule.

## Stage 4 — Explainability & Decision Intelligence

- Objective: explain approved model behavior and provide constrained scenario analysis.
- Depends on: Sacred Gate 1.
- Representative steps: global and local SHAP analysis; fidelity validation; reason abstraction; non-causal limitation controls; feasible scenario and counterfactual engine.
- Expected deliverables: explanation services, model-governance evidence, scenario rules, tests, and limitations.
- Gate direction: explanations faithfully reflect the approved model; scenarios are deterministic, feasible, and never represented as causal guarantees.
- Deferred to the plan: explanation interfaces, reason taxonomy, feasibility rules, and thresholds.

## Stage 5 — Policy, Regulatory Knowledge & Grounding

- Objective: build separate deterministic policy execution and evidence retrieval capabilities.
- Depends on: domain definitions and approved interfaces from earlier stages.
- Representative steps: version fictional internal policy; encode and test rules; generate reason codes; identify authoritative regulatory sources; ingest with provenance; retrieve citations; test abstention and source drift.
- Expected deliverables: fictional policy corpus, deterministic rule engine, regulatory corpus, retrieval system, evaluation evidence.
- Gate direction: rule execution is deterministic and traceable; retrieval is grounded and cited; neither path is confused with the other.
- Deferred to the plan: policies, jurisdiction, sources, rule schema, retrieval design, and thresholds.

## Stage 6 — Application Services, Persistence & Audit

- Objective: expose stable deterministic interfaces and preserve reconstructable system state.
- Depends on: approved model, explanation, scenario, policy, and retrieval contracts.
- Representative steps: domain services; FastAPI contracts; provisional SQLite persistence; version tracking; audit events; authorization and data boundaries; decision reconstruction.
- Expected deliverables: service API, persistence layer, audit trail, contracts, tests.
- Gate direction: services preserve upstream authority, records are traceable, and a decision context can be reconstructed.
- Deferred to the plan: schemas, API routes, authentication, migrations, retention, and PostgreSQL revisit evidence.

## Stage 7 — AI-Assisted Human Underwriting

- Objective: deliver grounded AI assistance inside an explicit human-review workflow.
- Depends on: stable Stage 6 services plus approved upstream deterministic components.
- Representative steps: typed copilot tools; grounded explanations; abstention; prohibited-behavior evaluation; provisional React/TypeScript/Vite interface; human decisions and audit capture; end-to-end workflow.
- Expected deliverables: copilot orchestration, evaluation harness, reviewer UI, integrated workflow tests.
- Gate: Sacred Gate 2 — Grounding & Decision Authority, plus approved end-to-end usability and workflow evidence.
- Deferred to the plan: LLM, prompts, tool schema, UI detail, harness cases, and thresholds.

## Stage 8 — Integrated Governance, Evaluation & Portfolio Release

- Objective: demonstrate the complete system responsibly and reproducibly.
- Depends on: all earlier stage gates.
- Representative steps: integrated acceptance and responsible-AI evaluation; security and privacy review; zero-cost CI; packaging; clean-environment verification; portfolio and interview documentation; readiness assessment.
- Expected deliverables: release evidence, reproducible demo, packaging, final limitations, portfolio narrative.
- Gate direction: complete local build and acceptance suite pass; Sacred Gate 2 is repeated; claims match evidence; remaining risks are explicit.
- Deferred to the plan: deployment target, optional hosted demo, packaging details, and release thresholds.

## Sacred gates

Sacred Gate 1 blocks downstream reliance on model risk outputs until Credit Model Integrity is proven against pre-approved criteria.

Sacred Gate 2 blocks completion of the AI-assisted product until Grounding & Decision Authority is proven against pre-approved criteria.

Neither gate receives final thresholds in this roadmap. The relevant approved stage plan must define them before evaluation begins.

## Roadmap changes

A material change to stage capabilities, dependency order, or a sacred gate requires explanation and approval. Preserve historical approved plans, update current architecture when appropriate, and record the deviation in the affected explainer and stage summary.
