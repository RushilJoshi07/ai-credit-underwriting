# Credit Product Scope

## Purpose and authority

This document is authoritative for the project's current credit-product framing. It evaluates the repository's provisional unsecured-personal-lending assumption without forcing the evidence toward that result.

Competition provenance and population evidence live in [the source assessment](../data/home-credit-source-assessment.md). Target meaning lives in [the target-semantics assessment](../data/home-credit-target-semantics.md). Canonical source metadata lives in [the source register](../data/home-credit-source-register.md).

## Current status

**Remains provisional**

The evidence supports a historical loan-repayment prediction task in a Home Credit consumer-finance context. It does not establish that every current application is an unsecured personal loan, and it does not establish a materially different dataset-specific product framing strongly enough to reframe the architecture.

## Repository-established framing

The repository entered Stage 1 with unsecured personal lending as a provisional product context. Governance permits evidence to confirm, narrow, reframe, reject, or leave that context provisional.

This is a repository constraint, not a fact about the source data.

## Evaluation criteria

The assessment considered:

- whether borrowers are private individuals;
- whether the source is situated in consumer finance;
- whether the current applications are loans;
- whether the current product family is identified;
- whether secured or unsecured status is established;
- whether multiple product types appear;
- whether the dataset geography, lender entity, and historical period are known;
- whether the source supports the proposed demonstration narrative without overclaiming.

## Evidence assessment

### Borrower and market context

The competition overview refers broadly to applicants, loans, clients with limited credit histories, repayment ability, and financial inclusion. [HC-SRC-001](../data/home-credit-source-register.md#hc-src-001--original-competition-overview-and-evaluation)

Home Credit Group's 2018 annual report describes the broader group as a consumer-finance provider whose principal credit exposure was consumer financing to private individuals. [HC-SRC-004](../data/home-credit-source-register.md#hc-src-004--home-credit-group-2018-annual-report)

These sources support a broad consumer-finance context. The corporate report does not establish the competition sample's inclusion criteria.

### Current-loan context

The official data page says one row in the main application data represents one loan in the sample. [HC-SRC-002](../data/home-credit-source-register.md#hc-src-002--original-competition-data-page)

That supports describing the main unit as a loan. It does not establish the loan's product family, purpose, collateral status, or legal classification.

### Product breadth

The official data description identifies historical supporting data involving POS and cash loans, credit cards, external credits, and prior Home Credit applications. [HC-SRC-002](../data/home-credit-source-register.md#hc-src-002--original-competition-data-page)

The 2018 annual report separately identifies several group-wide product classes, including POS, revolving, cash, car, and mortgage loans. [HC-SRC-004](../data/home-credit-source-register.md#hc-src-004--home-credit-group-2018-annual-report)

This establishes product breadth in the surrounding source context. It does not prove that every category occurs as the current modeled loan.

### Secured or unsecured status

The corporate report describes group-level collateral composition and says some product categories can be secured while others are unsecured. [HC-SRC-004](../data/home-credit-source-register.md#hc-src-004--home-credit-group-2018-annual-report)

No inspected dataset-specific source maps those group statements to the current application rows. The competition sample's secured or unsecured status therefore remains unresolved.

## Outcome classification

### Confirmed

Not selected. Dataset-specific evidence does not establish that the current sample consists of unsecured personal loans.

### Narrowed

Not selected. The evidence does not identify a defensible unsecured-personal-loan subset at this stage.

### Reframed

Not selected. “Consumer finance” is well supported as broad source context, but the evidence does not yet define a sufficiently precise replacement product scope for the modeled current applications. Treating broad corporate context as the dataset's product definition would overstate the evidence.

### Rejected

Not selected. No authoritative evidence establishes that unsecured personal lending is impossible or fundamentally incompatible with the source.

### Remains provisional

Selected. Unsecured personal lending remains a project hypothesis awaiting dataset-specific product and collateral evidence. The safe current evidence description is a historical Home Credit loan-repayment task within a broader consumer-finance context.

## Claim-to-source traceability

### Claim HC-PS-001

- Claim: The official task concerns applicants and loans in a repayment-ability context.
- Classification: Direct source statement
- Supporting source IDs: HC-SRC-001
- Qualification: This does not identify the loan product or target event.

### Claim HC-PS-002

- Claim: One row in the main application data is described as one loan in the sample.
- Classification: Direct source statement
- Supporting source IDs: HC-SRC-002
- Qualification: Observed file grain will be tested only after authorized acquisition.

### Claim HC-PS-003

- Claim: Home Credit's broader 2018 business context was consumer financing to private individuals across multiple product classes and geographies.
- Classification: Direct source statement
- Supporting source IDs: HC-SRC-004
- Qualification: Group-wide context is not competition-sample composition.

### Claim HC-PS-004

- Claim: The official competition data description includes historical supporting data from multiple credit-product categories.
- Classification: Direct source statement
- Supporting source IDs: HC-SRC-002
- Qualification: Historical product breadth does not establish the current loan's product type.

### Claim HC-PS-005

- Claim: The current sample's secured or unsecured status is unresolved.
- Classification: Unresolved ambiguity
- Supporting source IDs: HC-SRC-001, HC-SRC-002, HC-SRC-004
- Qualification: No inspected dataset-specific source provides this mapping.

### Claim HC-PS-006

- Claim: Unsecured personal lending remains provisional.
- Classification: Provisional assumption and repository constraint
- Supporting source IDs: HC-SRC-001, HC-SRC-002, HC-SRC-004
- Qualification: Evidence supports a broad consumer-finance loan context but neither confirms nor materially disproves the narrower framing.

### Claim HC-PS-007

- Claim: The dataset must not be represented as U.S. bank customers, a named lender's current population, or a production population.
- Classification: Repository constraint reinforced by unresolved source-population evidence
- Supporting source IDs: HC-SRC-001, HC-SRC-002, HC-SRC-004
- Qualification: The inspected sources do not identify a transferable dataset population.

## Supported language

- “Historical Home Credit competition data”
- “Loan-repayment prediction task”
- “Consumer-finance context,” with a source citation
- “Unsecured personal lending is the project's provisional product framing”
- “The current-application product and collateral status remain unresolved”

## Unsupported language

- “The dataset is an unsecured-personal-loan dataset”
- “All current applications are cash loans”
- “All loans are unsecured”
- “The sample represents a specific Home Credit country operation”
- “The sample represents U.S. bank customers”
- “The data represents current lending conditions”
- “The source population is representative of the planned demo population”

## Population and transfer limitations

The source does not establish a country, operating entity, sampling frame, application period, or representative deployment population. A model trained on it cannot inherit those missing facts from Home Credit's group-wide business description.

Synthetic demonstration identities and workflow fields remain separate from historical source data. The provisional product narrative cannot be used to relabel historical rows or invent missing source attributes.

## Architecture assessment

No architecture amendment is required at this step.

The architectural statement already labels unsecured personal lending provisional and requires Stage 1 evidence before stronger claims. This assessment leaves that status unchanged. If later authorized field-level evidence confirms, narrows, reframes, or rejects the scope, the approved architecture-amendment process applies before `docs/architecture.md` changes.

## Consequences for later stages

- Step 2 must not treat the provisional product framing as a licensing conclusion.
- Steps 3–6 may gather dataset-specific evidence that changes this status.
- Stage 2 must select any modeling cohort only through its approved plan.
- UI or synthetic demo work must not imply that the historical data contains unsecured-personal-loan identities or workflow fields.

## Open questions

- What current-loan product categories occur in the training and test application tables?
- Does official field documentation establish collateral status?
- Does the sample come from one or several countries or operating entities?
- What historical period and applicant-selection process produced the sample?
- Can an evidence-backed modeling cohort later align with unsecured personal lending?
