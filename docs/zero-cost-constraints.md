# Zero-Cost Constraints

## Purpose

The complete required core must be buildable and runnable for `$0`. Cost is an architectural constraint, not a preference to evaluate only at release time.

## Required core

The required workflow must have a documented local path and must not depend on:

- paid APIs or model inference;
- paid databases or vector stores;
- paid experiment tracking or monitoring;
- paid hosted deployment;
- a free trial that later requires payment;
- proprietary hosted functionality with no local replacement.

The project may use free and open-source local tools such as Python, scikit-learn, justified LightGBM or XGBoost candidates, SHAP, FastAPI, SQLite, local MLflow, Ollama, sentence-transformers, FAISS, React, TypeScript, Vite, and Docker.

Listing a tool here does not pre-approve its implementation details or settle open architecture choices.

## Optional services

An optional hosted or paid integration must be isolated from the core. Documentation must state:

- that it is optional;
- its possible cost or quota;
- the free local replacement;
- what functionality is unavailable without it;
- how to disable it.

Introducing a possible cost requires explanation and approval before it becomes part of the project.

## Free tiers

GitHub and GitHub Actions may be used where free usage is sufficient. Essential tests and verification must remain runnable locally. A hosted quota, pricing change, or service outage must not make the core impossible to build or verify.

## Data, storage, and compute

- Do not commit large datasets or generated artifacts merely to avoid external storage design.
- Document reproducible acquisition, provenance, checksums, and transformation metadata instead.
- Prefer models that can run on documented local hardware constraints.
- Make expensive optional experiments separable from the required demonstration path.
- Treat local disk, memory, and runtime as real constraints even when no money is charged.

## Dependency review

Before adding a required dependency, explain:

- its role and license;
- whether installation and core use are free;
- whether an account or credit card is required;
- whether data leaves the local environment;
- local hardware requirements;
- maintenance and lock-in risks;
- realistic free alternatives;
- how the system behaves if it is unavailable.

## Generated local artifacts

Project-local datasets, databases, model binaries, MLflow runs, vector indexes, embeddings, logs, and local model-runtime artifacts should be excluded from Git by default while their schemas, configuration, source code, manifests, and reproducibility metadata remain trackable.

This repository does not manage or modify global machine-level Ollama, model, or package caches outside the repository.

## Revisit rule

If a later requirement appears to need a paid service, stop and propose alternatives. The user must explicitly approve any change, and the required core must retain a `$0` path unless the governing project constraint itself is formally changed.
