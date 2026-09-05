# Home Credit Source Register

## Purpose and authority

This register is the canonical inventory of sources evaluated during Stage 1 Step 1. It records source identity, authority, access status, relevance, and limitations. It does not decide what `TARGET` means, define the project product scope, or interpret access and publication rights.

The evidence documents cite the stable source IDs below. A source ID identifies a source; it does not imply that the source supports every claim made near its citation.

## Registration conventions

- Access dates use ISO `YYYY-MM-DD` format.
- `Inspected` means the relevant content was directly viewed at the registered URL.
- `Partially inspected` means public metadata or description was visible but a relevant artifact or view was access-gated.
- `Deferred` means the source is authoritative but intentionally reserved for a later approved step.
- `Lead only` means the source helped locate or characterize a question but is not authority for a substantive conclusion.
- `Rejected for this claim` means the source may be genuine but cannot establish facts about this competition or dataset.

## Approved authority hierarchy

1. Original competition overview and evaluation
2. Original competition data page
3. `HomeCredit_columns_description.csv` from the authorized official bundle
4. Original competition-specific and general rules
5. Original sponsor documentation directly addressing this dataset
6. Competition-host clarifications with established authorship
7. Secondary material only as a lead

More specific dataset evidence controls over broad corporate context when both address the same question. Silence or missing access is recorded as uncertainty, not filled with a lower-authority assertion.

## Authoritative sources inspected

### HC-SRC-001 — Original competition overview and evaluation

- Title: Home Credit Default Risk
- Publisher/platform: Kaggle
- Competition host displayed by Kaggle: Home Credit Group
- Authority level: 1 — original competition overview and evaluation
- URL: https://www.kaggle.com/competitions/home-credit-default-risk/overview/description
- Access date: 2026-09-05
- Access status: Inspected without authentication
- Relevance: competition framing, start and close dates, host display, evaluation description, submission identifier, and requested `TARGET` probability
- Limitation: does not define the target classes, horizon, product type, dataset geography, or representativeness; the live page may also reflect later platform presentation changes
- Supports: broad repayment-ability framing; use of `SK_ID_CURR`; evaluation of predicted probability against the observed target; official competition identity
- Does not support: exact `TARGET=1` or `TARGET=0` rule; prediction horizon; a legal or business default definition; a particular product type; dataset geography; representativeness
- Version limitation: the live page was accessed after the 2018 competition and may reflect platform presentation changes

### HC-SRC-002 — Original competition data page

- Title: Home Credit Default Risk — Data
- Publisher/platform: Kaggle
- Competition host displayed by Kaggle: Home Credit Group
- Authority level: 2 — original competition data page
- URL: https://www.kaggle.com/competitions/home-credit-default-risk/data
- Access date: 2026-09-05
- Access status: Partially inspected without authentication
- Relevance: public dataset description, train/test role, row-grain description, named supporting tables, official column-description artifact, and access gate
- Limitation: the field-level artifact preview was access-gated, and the public description does not define the target classes, horizon, or current-loan product mix
- Supports: `TARGET` is present in the training main table and absent from the test main table; one main-table row represents one loan in the sample; supporting history includes multiple credit-product categories
- Does not support: exact target rule or horizon; the product type of every current sample loan; dataset geography; source-population representativeness
- Access limitation: the selected column-description file preview displayed a sign-in and competition-rules acceptance requirement

### HC-SRC-003 — Original competition rules

- Title: Home Credit Default Risk — Competition Rules
- Publisher/platform: Kaggle
- Competition sponsor displayed in the rules: Home Credit International a.s.
- Authority level: 4 — original competition-specific and general rules
- URL: https://www.kaggle.com/competitions/home-credit-default-risk/rules
- Access date: 2026-09-05
- Access status: Inspected without authentication for competition provenance only
- Relevance: competition identity, named sponsor, and Kaggle hosting relationship
- Limitation: legal access and use terms require the separate Step 2 assessment; this project does not provide legal advice
- Step 1 boundary: no conclusion about present access, licensing, portfolio use, or publication permission is made here
- Deferred use: the access, use, licensing, and publication analysis belongs to Stage 1 Step 2

### HC-SRC-004 — Home Credit Group 2018 annual report

- Title: Home Credit Group B.V. Annual Report for the fifteen-month period from 1 October 2017 to 31 December 2018
- Publisher: Home Credit Group B.V.
- Authority level: 5 — original sponsor-related corporate documentation
- URL: https://www.homecredit.net/wp-content/uploads/2022/12/HC-Group-BV-IFRS-2018-Q4-15M-without-auditor-signature.pdf
- Access date: 2026-09-05
- Access status: Inspected
- Relevance: pages 2–5 for business and geographic context; 52–53 for customer and product classes; 61–62 for portfolio concentration and collateral context
- Limitation: this is group-level corporate reporting, not documentation of competition-sample composition
- Supports: Home Credit Group described a broad consumer-finance business serving private individuals across multiple geographies and product classes around the competition period
- Does not support: which group entity supplied the competition rows; dataset countries; dataset sampling dates; the product mix of the competition's current applications; exact target semantics or horizon
- Scope limitation: corporate portfolio statements must not be silently transferred to the competition sample

## Authoritative source deferred

### HC-DEFERRED-001 — Official column-description artifact

- Title: `HomeCredit_columns_description.csv`
- Publisher/source: listed in the official Kaggle competition bundle
- Authority level: 3 — official field-level documentation
- Canonical page: https://www.kaggle.com/competitions/home-credit-default-risk/data?select=HomeCredit_columns_description.csv
- Access date: 2026-09-05
- Access status: Deferred; preview required sign-in and agreement to competition rules
- Relevance: expected to contain the field-level description needed to test the exact `TARGET` event and coding rule
- Limitation: its contents were not inspected, so it supports no present semantic conclusion
- Handling: not downloaded, copied from a mirror, or treated as inspected
- Next eligible review: after Step 2 defines the access contract and Step 3 performs authorized acquisition

## Secondary lead not used as authority

### HC-LEAD-001 — Participant solution write-up

- Title: Pseudo Data Augmentation (27th place short writeup)
- Author: Kaggle participant `nyanp`
- Platform: Kaggle
- Authority level: 7 — secondary lead only
- URL: https://www.kaggle.com/competitions/home-credit-default-risk/writeups/nyanp-pseudo-data-augmentation-27th-place-short-wr
- Access date: 2026-09-05
- Access status: Inspected as a research lead
- Relevance: attributes a target definition to the official column-description file
- Limitation: participant-authored material cannot establish dataset semantics
- Use in Step 1: establishes only that the deferred official artifact may answer the target question
- Prohibited use: its reproduced wording does not establish `TARGET=1`, `TARGET=0`, thresholds, horizon, or permitted project terminology

## Sources rejected for substantive conclusions

### HC-REJECTED-001 — Different Home Credit competition

- Title: Home Credit — Credit Risk Model Stability
- Publisher/platform: Kaggle
- Authority level: original source for a different competition; rejected for the 2018 dataset
- URL: https://www.kaggle.com/competitions/home-credit-credit-risk-model-stability
- Access date: 2026-09-05
- Access status: Evaluated and rejected for this dataset
- Relevance: checked to determine whether later official Home Credit competition material clarified the earlier target
- Limitation: it concerns a different dataset and target
- Reason: it is a later competition with a different dataset and target. Its terminology cannot define the 2018 Home Credit Default Risk `TARGET`.

### HC-REJECTED-002 — Current corporate About Us page

- Title: About Us
- Publisher: Home Credit
- Authority level: original corporate source; rejected for dataset-specific claims
- URL: https://www.homecredit.net/about-us.aspx/
- Access date: 2026-09-05
- Access status: Inspected and rejected as evidence about the 2018 competition sample
- Relevance: checked for sponsor business context
- Limitation: current broad corporate content is neither period-specific nor dataset-specific
- Reason: it describes Home Credit broadly at the access date but does not document this dataset's population, products, target, or horizon.

## Sources not located

- No competition-host clarification with established sponsor or organizer authorship was located that defines the 2018 `TARGET` event or prediction horizon.
- No public original sponsor document directly tying the competition sample to a specific country, operating entity, product class, or collateral status was located.

These are search outcomes, not proof that such documents never existed.

## Maintenance rules

- New evidence receives a new stable source ID.
- A URL change does not erase the original access record.
- Later access to `HC-DEFERRED-001` must be recorded without rewriting this Step 1 access history.
- Evidence documents must assign source IDs to individual material conclusions.
- Step 2 owns access, licensing, publication, and acquisition-contract conclusions.
