# Interview Learning Standard

## Purpose

This project is both an engineering system and a structured learning exercise. Explanations must help a beginner develop transferable judgment rather than memorize project-specific answers.

## Teaching behavior

Before non-trivial implementation:

- define new terms in plain language;
- connect the step to the product and architecture;
- explain why it is needed now;
- compare realistic alternatives;
- identify failure modes and tradeoffs;
- explain how tests will establish evidence.

Do not hide uncertainty or assume prior knowledge. Introduce detail progressively without replacing precision with oversimplification.

## Connect reasoning to implementation

Every meaningful step should enable the learner to explain:

- the requirement being addressed;
- the component's responsibility and boundaries;
- its inputs, outputs, and dependencies;
- why the chosen design fits;
- what alternatives were considered;
- how the implementation works at an important-code level;
- how tests and verification support the claim;
- remaining limitations and future dependencies.

## Interview questions and answers

Step explainers must include likely interview questions and strong answers. A strong answer should:

- begin with the decision or outcome;
- explain the relevant concept accurately;
- connect it to concrete project evidence;
- include the main tradeoff;
- state limitations without undermining the valid result;
- avoid claiming unimplemented or unproven capability.

Answers should be concise enough to deliver aloud, with optional deeper follow-up detail.

## Senior-level follow-ups

Explain senior questions that probe:

- failure modes and edge cases;
- data or target leakage;
- reproducibility and audit evidence;
- changing scale or concurrency requirements;
- security, privacy, and governance;
- monitoring and model drift;
- rollback and version compatibility;
- deterministic versus generative authority;
- fairness evidence and representativeness;
- why a reasonable alternative was deferred.

A senior answer should discuss conditions under which the current decision should change rather than defending it as universally correct.

## Common misconceptions

Learning material must actively avoid these errors:

- treating predictive performance as probability calibration;
- treating SHAP as causal explanation;
- treating a retrieved passage as executable policy;
- treating an LLM explanation as a lending decision;
- treating synthetic identity data as verified source data;
- assuming Home Credit represents a specific modern lending population;
- describing a passing test as proof of production readiness;
- describing responsible-AI metrics as legal certification.

## Stage-level interview defense

Each stage summary should support a coherent explanation of:

- the capability built;
- why its stages and steps were ordered that way;
- important decisions and approved deviations;
- gate evidence;
- what was and was not proven;
- what the next capability may safely trust.

## Honest claims

Interview preparation must match repository evidence. Never invent scale, users, production incidents, regulatory approval, model quality, or test results. It is stronger to explain a limitation and the next verification step than to exaggerate completeness.

## Learning quality check

Before completing a step, ask whether a beginner could use its explainer to describe the concept, implementation, evidence, tradeoffs, and limitations without needing the original conversation. If not, improve the explainer before commit.
