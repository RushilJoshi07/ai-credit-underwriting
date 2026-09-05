# Home Credit TARGET Semantics

## Purpose and authority

This document is authoritative for the project's current interpretation of Home Credit `TARGET`, its prediction horizon, and permitted terminology. It records the strongest conclusion supported by inspected authoritative sources without importing conventions from secondary material.

Source metadata lives in [the source register](home-credit-source-register.md). Competition provenance and population limitations live in [the source assessment](home-credit-source-assessment.md).

## Current conclusion

- `TARGET=1` status: **Unresolved**
- `TARGET=0` status: **Unresolved business meaning**
- Prediction-horizon status: **Unresolved**
- “Default” status: **Prohibited as a project interpretation of `TARGET`**
- “Probability of default” or “PD” status: **Prohibited**

The official public pages inspected in Step 1 establish that the competition predicts a probability for `TARGET` in a repayment-ability context. They do not provide the field-level event rule or a time horizon. [HC-SRC-001](home-credit-source-register.md#hc-src-001--original-competition-overview-and-evaluation)

## Questions investigated

- What event makes `TARGET=1`?
- What business meaning, if any, is independently assigned to `TARGET=0`?
- Does `TARGET=0` mean only “not labeled `TARGET=1`”?
- Does the outcome concern the loan represented by the current main-table row?
- Is a prediction point defined?
- Is an observation or performance horizon defined?
- Are event thresholds or installment counts specified?
- Can “default,” “probability of default,” or “PD” be used accurately?

## Authoritative evidence inspected

The competition overview says submissions are evaluated using the predicted probability and observed target, and asks for a `TARGET` probability for each `SK_ID_CURR`. It frames the broader objective as predicting repayment ability. [HC-SRC-001](home-credit-source-register.md#hc-src-001--original-competition-overview-and-evaluation)

The data page says the training main table contains `TARGET`, the test main table does not, and one main-table row represents one loan in the sample. It does not display the field-level target rule in the public description. [HC-SRC-002](home-credit-source-register.md#hc-src-002--original-competition-data-page)

The official column-description artifact was listed but its preview required sign-in and acceptance of competition rules. It was not downloaded or replaced with a mirrored copy. [HC-DEFERRED-001](home-credit-source-register.md#hc-deferred-001--official-column-description-artifact)

## TARGET=1 assessment

The inspected authoritative sources do not define the event that produces `TARGET=1`. The competition title and repayment narrative are too broad to supply that definition.

Therefore:

- `TARGET=1` must remain the source label.
- It may be described as the positive class only as a structural label, not as a business event.
- No days-past-due threshold, installment count, delinquency condition, default event, or outcome window is established.
- A later authorized inspection of the official field-description artifact may resolve or narrow this conclusion.

## TARGET=0 assessment

The inspected authoritative sources do not provide an independent business interpretation of `TARGET=0`, and the official coding rule itself was not available for inspection.

Therefore:

- `TARGET=0` must remain the source label.
- It must not be translated into “successful repayment,” “fully repaid,” “paid on time,” “non-defaulting borrower,” or an equivalent stronger claim.
- If later authoritative evidence defines `TARGET=1` and identifies 0 only as all other cases, the approved interpretation will be the complementary non-`TARGET=1` class—not proof of successful repayment.
- Absence of an independent `TARGET=0` business definition is a limitation, not by itself a Stage 1 failure.

## Prediction-point assessment

The data page says one main-table row represents one loan and describes some supporting credit-bureau records as existing before the application date. That suggests an application-related analytical context, but it does not define a complete feature-availability cutoff for the current loan. [HC-SRC-002](home-credit-source-register.md#hc-src-002--original-competition-data-page)

Current status: **Supported inference, not direct source definition.** The likely prediction point is associated with the current application, but Stage 2 must not rely on that assumption until Stage 1 timing and leakage work establishes field availability.

## Prediction-horizon assessment

The competition overview, evaluation, and public data description inspected in Step 1 do not state how far into the future the outcome is observed. No exact or bounded period can be derived from the visible authoritative evidence.

Current status: **Unresolved.**

This is not “inferred only,” because there is no authoritative time statement from which a defensible period can be inferred. It is not “conflicting,” because no competing authoritative horizons were found.

## Source wording, inference, and ambiguity

### Direct source statements

- Kaggle asks for a probability for `TARGET` for each test-set `SK_ID_CURR`. HC-SRC-001.
- Kaggle evaluates predicted probability against the observed target. HC-SRC-001.
- The training main table contains `TARGET`; the test main table does not. HC-SRC-002.
- One main-table row is described as one loan in the sample. HC-SRC-002.

### Supported inference

- The modeling context concerns a current loan/application and historical information associated with its applicant. HC-SRC-001 and HC-SRC-002.
- Qualification: the exact prediction cutoff and feature availability remain unverified.

### Provisional assumption

- The likely prediction point is the current application decision.
- Qualification: this assumption cannot authorize Stage 2 features until leakage evidence establishes timing.

### Unresolved ambiguity

- Exact event for `TARGET=1`.
- Independent business meaning, if any, for `TARGET=0`.
- Target coding rule.
- Observation or prediction horizon.
- Whether target thresholds are anonymized.
- Whether the outcome is censored or incomplete.

### Repository constraints

- Retain the name `TARGET` until authoritative evidence supports another label.
- Do not claim default or a horizon without evidence.
- Do not describe the source as a production or U.S.-bank population.

## Claim-to-source traceability

### Claim HC-TS-001

- Claim: The official task requests a predicted probability for `TARGET` for each `SK_ID_CURR`.
- Classification: Direct source statement
- Supporting source IDs: HC-SRC-001
- Qualification: A requested probability submission does not prove calibration or define the event.

### Claim HC-TS-002

- Claim: `TARGET` is present in the training main table and absent from the test main table.
- Classification: Direct source statement
- Supporting source IDs: HC-SRC-002
- Qualification: Actual file contents have not been acquired or validated.

### Claim HC-TS-003

- Claim: Exact `TARGET=1` semantics are unresolved.
- Classification: Unresolved ambiguity
- Supporting source IDs: HC-SRC-001, HC-SRC-002, HC-DEFERRED-001
- Qualification: The most relevant official field-level artifact remains deferred.

### Claim HC-TS-004

- Claim: `TARGET=0` has no independently verified business meaning in the inspected sources.
- Classification: Unresolved ambiguity
- Supporting source IDs: HC-SRC-001, HC-SRC-002, HC-DEFERRED-001
- Qualification: It cannot currently be described even as a verified complementary class because the official coding rule was not inspected.

### Claim HC-TS-005

- Claim: The prediction horizon is unresolved.
- Classification: Unresolved ambiguity
- Supporting source IDs: HC-SRC-001, HC-SRC-002, HC-DEFERRED-001
- Qualification: Neither an exact nor bounded outcome period appears in the inspected public official material.

### Claim HC-TS-006

- Claim: The likely prediction point is associated with the current application.
- Classification: Supported inference
- Supporting source IDs: HC-SRC-001, HC-SRC-002
- Qualification: Field-level timing remains subject to later leakage review.

### Claim HC-TS-007

- Claim: “Default,” “probability of default,” and “PD” are prohibited target labels at this point.
- Classification: Repository constraint supported by unresolved evidence
- Supporting source IDs: HC-SRC-001, HC-SRC-002, HC-DEFERRED-001
- Qualification: A later change requires authoritative event and horizon evidence plus the approved change process.

## Allowed terminology

- `TARGET`
- `TARGET=1` and `TARGET=0` as uninterpreted source labels
- “observed target,” when describing Kaggle's evaluation
- “predicted probability for `TARGET`,” when describing the competition submission requirement
- “repayment-ability context,” when clearly attributed to the broad competition framing
- “historical Home Credit competition data”

## Prohibited terminology

Unless later authoritative evidence changes the conclusion, do not call `TARGET` or either class:

- default;
- loan default;
- probability of default;
- PD;
- bad borrower or good borrower;
- successful repayment;
- fully repaid;
- paid on time;
- non-defaulting borrower.

The words may appear in documentation when explaining why they are prohibited or when distinguishing Home Credit's general corporate risk terminology from this dataset's unverified label.

## Criteria for revisiting default and PD language

“Default” requires authoritative, dataset-specific evidence establishing the event and material qualifications.

“Probability of default” or “PD” additionally requires a documented horizon and relevant population context. Even if those semantic prerequisites are later met, Step 1 cannot establish that a future model produces a valid probability. Calibration and model validity belong to later approved modeling stages.

## Secondary evidence handling

HC-LEAD-001 reproduces wording that it attributes to the official column-description artifact. Because it is a participant-authored write-up rather than the original artifact, it was used only to confirm that inspecting HC-DEFERRED-001 is important. None of its asserted thresholds, class meanings, or wording is adopted here.

## Consequences for later stages

- Step 2 must determine legitimate access without relying on this semantic assessment as a rights conclusion.
- Step 3 may acquire the official bundle only under the approved access contract.
- Once HC-DEFERRED-001 is legitimately inspected, the target document may be updated with new evidence while preserving this Step 1 explainer as execution history.
- Stage 2 must quarantine fields whose availability at the inferred prediction point is not established.
- Stage 3 must not describe a model as estimating default or PD unless both semantic and model-validity requirements are satisfied.

## Limitations

The strongest field-level authoritative source was unavailable without authentication and rules acceptance. The exact positive-class rule, negative-class rule, thresholds, horizon, and censoring behavior remain unknown. This document makes those absences explicit rather than filling them with common competition terminology.
