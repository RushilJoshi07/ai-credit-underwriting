# Home Credit Source Assessment

## Purpose and authority

This document is authoritative for Stage 1 findings about the competition's provenance, source roles, broad context, and population limitations. It does not define licensing rights, the exact `TARGET` rule, or the final product architecture.

Source identity and access metadata live in [the source register](home-credit-source-register.md). Detailed target conclusions live in [the target-semantics assessment](home-credit-target-semantics.md). Product framing lives in [the credit-product scope assessment](../domain/credit-product-scope.md).

## Evidence classifications

- **Direct source statement:** explicitly stated in an inspected authoritative source.
- **Supported inference:** a narrow conclusion reasoned from cited authoritative statements.
- **Provisional assumption:** useful project framing not yet established by source evidence.
- **Unresolved ambiguity:** available evidence does not support one reliable conclusion.
- **Repository constraint:** inherited from approved governance rather than discovered externally.

## Research method

The research followed the hierarchy in `docs/plans/stage-1-plan.md`. Original Kaggle competition pages were inspected before sponsor-related corporate material. One secondary write-up was used only to locate a likely official field definition; its wording was not adopted as fact.

The official column-description artifact was not publicly viewable in the inspected unauthenticated session. It was deferred rather than obtained from an unofficial mirror.

## Competition and source provenance

The inspected evidence supports this narrow provenance chain:

- Kaggle presents Home Credit Default Risk as a 2018 featured prediction competition and displays Home Credit Group as the competition host. [HC-SRC-001](home-credit-source-register.md#hc-src-001--original-competition-overview-and-evaluation)
- The competition rules name Home Credit International a.s. as the competition sponsor and describe Kaggle as the hosting platform. [HC-SRC-003](home-credit-source-register.md#hc-src-003--original-competition-rules)
- Kaggle's official data page is the original public description of the competition bundle and lists the official column-description artifact. [HC-SRC-002](home-credit-source-register.md#hc-src-002--original-competition-data-page)

These facts establish competition provenance. They do not establish which Home Credit operating entity produced each row, which country or countries the sample covers, or how the sample was selected.

## Competition task context

The competition overview frames the task around estimating applicants' repayment abilities. Its evaluation compares a predicted probability with the observed target, and the submission uses `SK_ID_CURR` with a `TARGET` value. [HC-SRC-001](home-credit-source-register.md#hc-src-001--original-competition-overview-and-evaluation)

The data page states that the main data is divided into a training file containing `TARGET` and a test file without it, with one row representing one loan in the sample. It also describes historical supporting tables for external credits, prior Home Credit applications, POS and cash loans, credit cards, and installment payments. [HC-SRC-002](home-credit-source-register.md#hc-src-002--original-competition-data-page)

The overview's repayment language is broad problem framing. It is not a field-level definition of `TARGET`, and it does not identify a prediction horizon.

## Sponsor-related corporate context

Home Credit Group's 2018 annual report describes the group as a consumer-finance business operating across several geographic segments. It says the majority of group credit-risk exposure arose from consumer financing to private individuals and identifies significant loan classes including POS, revolving, cash, car, and mortgage loans. [HC-SRC-004](home-credit-source-register.md#hc-src-004--home-credit-group-2018-annual-report)

That report is useful historical context because its reporting period overlaps the competition year. It is not competition-sample documentation. Its group-wide product, geography, customer, delinquency, collateral, or accounting statements cannot be assigned to the competition rows without a dataset-specific source.

## Population and representativeness limitations

The inspected sources do not establish:

- the country or countries represented by the competition sample;
- the Home Credit legal entity or operating unit that supplied the sample;
- the sampling dates or observation window;
- the sampling method or inclusion and exclusion criteria;
- whether the rows represent all applicants, accepted loans, originated loans, or another selected cohort;
- the distribution of current-application product types;
- the collateral status of each current application;
- demographic or market representativeness;
- applicability to U.S. bank customers, a specific modern lender, or current lending conditions.

The annual report shows that the broader group operated across multiple markets and product classes. That makes transfer from group-level facts to a single unspecified dataset population especially unsafe. [HC-SRC-004](home-credit-source-register.md#hc-src-004--home-credit-group-2018-annual-report)

## Claim-to-source traceability

### Claim HC-SA-001

- Claim: Home Credit Default Risk was presented by Kaggle as a 2018 competition hosted by Home Credit Group.
- Classification: Direct source statement
- Supporting source IDs: HC-SRC-001
- Qualification: “Host” is Kaggle's displayed role label; the rules separately name the legal competition sponsor.

### Claim HC-SA-002

- Claim: The rules name Home Credit International a.s. as sponsor and Kaggle as hosting platform.
- Classification: Direct source statement
- Supporting source IDs: HC-SRC-003
- Qualification: Used only for provenance in Step 1; rights and obligations are deferred to Step 2.

### Claim HC-SA-003

- Claim: The competition asks for a probability associated with `TARGET` and evaluates it against the observed target.
- Classification: Direct source statement
- Supporting source IDs: HC-SRC-001
- Qualification: This does not define the target event or prove probability calibration.

### Claim HC-SA-004

- Claim: The official main table is split into training data with `TARGET` and test data without `TARGET`, and its stated grain is one loan per row.
- Classification: Direct source statement
- Supporting source IDs: HC-SRC-002
- Qualification: File contents and actual grain have not been validated.

### Claim HC-SA-005

- Claim: The data documentation describes supporting history across several credit-product categories.
- Classification: Direct source statement
- Supporting source IDs: HC-SRC-002
- Qualification: Supporting-table product history does not establish the product type of every current application.

### Claim HC-SA-006

- Claim: Home Credit's broader business around the competition period included consumer financing to private individuals across multiple product classes and geographies.
- Classification: Direct source statement
- Supporting source IDs: HC-SRC-004
- Qualification: This is group-level corporate context, not proof of competition-sample composition.

### Claim HC-SA-007

- Claim: The competition sample's geography, operating entity, sampling method, and representativeness are unresolved.
- Classification: Unresolved ambiguity
- Supporting source IDs: HC-SRC-001, HC-SRC-002, HC-SRC-004
- Qualification: None of the inspected sources supplies dataset-specific answers to those questions.

### Claim HC-SA-008

- Claim: The project must not present the sample as U.S. bank customers, a named lender's current population, or a production population.
- Classification: Repository constraint
- Supporting source IDs: None required; governed by `AGENTS.md` and `docs/architecture.md`
- Qualification: Stage 1 evidence reinforces but does not originate this restriction.

## Supported general descriptions

The following descriptions are supportable when kept in context:

- “The Home Credit Default Risk competition is a historical loan-repayment prediction task.”
- “Kaggle asks for a probability for the source field named `TARGET`.”
- “The source is situated in Home Credit's consumer-finance context.”
- “The official data description includes current-loan rows and several forms of prior credit history.”

These phrases do not settle target semantics, product scope, or population transferability.

## Unsupported general descriptions

The evidence does not support saying that:

- the dataset represents U.S. banking;
- all current applications are unsecured personal loans;
- all source customers are unbanked;
- the sample covers a named country or time period;
- `TARGET` is a legal, accounting, or universal default definition;
- a model trained later would be production-ready or valid for a different population.

## Access and licensing boundary

The rules and data-access gate were observed because they establish source provenance and explain why an official artifact was deferred. Step 1 makes no determination about permission for portfolio use, publication, redistribution, or acquisition. Those questions belong exclusively to Stage 1 Step 2.

## Research limitations

- The official field-description file was not inspected.
- No authenticated Kaggle content was accessed.
- No dataset bytes were downloaded.
- No organizer-authored clarification defining `TARGET` or the sample population was located.
- The live pages were accessed years after the competition.
- Corporate reports describe the group, not necessarily the competition sample.

## Conclusion

The competition's official identity, broad task, train/test role, main-table stated grain, and source-host relationship are documented. Exact target semantics, horizon, current-application product mix, geography, sampling, and representativeness remain unresolved pending stronger dataset-specific evidence.
