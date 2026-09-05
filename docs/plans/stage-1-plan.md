# Stage 1 Plan — Credit Domain & Data Foundation

## Context entering the stage

Stage 0 is complete. The repository contains the approved governance, architecture, roadmap, workflow, documentation, learning, cost, and repository-hygiene foundation. It contains no application or data implementation.

Stage 1 must establish the factual, reproducible, and legally cautious raw-data foundation needed by later analytical and modeling work.

## Evidence status entering Stage 1

### Established by repository governance

- The provisional product context is unsecured personal lending.
- “LLM explains; deterministic systems decide.”
- Home Credit `TARGET` meaning and prediction horizon are unresolved.
- Historical source data, engineered model features, synthetic data, fictional policy, and authoritative regulatory material must remain separate.
- The required core must remain locally runnable for `$0`.
- Stage 1 establishes source meaning, provenance, acquisition, table relationships, raw-data validation, and leakage evidence.
- Stage 1 does not satisfy Sacred Gate 1. It supplies evidence needed by later modeling stages.

### Preliminary primary-source observations requiring formal Stage 1 documentation

- The official competition overview asks participants to predict `TARGET` for each `SK_ID_CURR` and evaluates submissions using ROC AUC. This does not by itself establish a legal definition of default, an exact outcome window, or a universal probability-of-default interpretation.
- The official data page currently lists ten CSV files, describes their broad row grains, labels the data as subject to competition rules, and requires users to agree to those rules before access.
- Kaggle currently documents authenticated CLI and KaggleHub access mechanisms.

These observations become repository-authoritative only after Stage 1 records and verifies them.

### Provisional assumptions

- The likely prediction point is the current application decision.
- The source may be useful for an unsecured-personal-lending demonstration.
- Authorized local educational access may be possible after the user reviews and accepts the applicable rules.

### Open decisions

- Exact `TARGET` event semantics
- Exact prediction horizon
- Whether “default” or “PD” is permitted terminology
- Permitted data use and publication
- Exact Python version
- Final raw-analysis engine
- Candidate tables for Stage 2
- Schema and anomaly thresholds
- Stage 2 split and transformation design

## Approved refinements

The final plan incorporates these reviewed refinements:

- The neutral domain document is `docs/domain/credit-product-scope.md`. Unsecured personal lending remains provisional inside it.
- Step 2 defines the access, licensing, publication, and acquisition contract. Step 3 implements that contract and performs authorized acquisition.
- The architectural requirement is memory-efficient, read-only analysis of the multi-GB source. DuckDB is the selected, replaceable Stage 1 implementation rather than a permanent architectural constraint.
- uv is the selected Stage 1 environment and dependency manager. It is an implementation choice rather than permanent system architecture.
- Raw snapshots are governed by a write-once/logically immutable contract without claiming filesystem-level immutability.
- Leakage review is risk-based. Unassessed fields remain quarantined and absence from a register never implies approval.
- `docs/architecture.md` changes only when evidence changes, resolves, or materially qualifies an architectural assumption or boundary. It does not become a dataset findings log.

These refinements do not conflict with Stage 0 governance.

## Stage objective

Stage 1 will determine:

- what the official source is;
- what `TARGET` supports us saying;
- what remains unknown about `TARGET` and its horizon;
- whether the provisional product framing remains defensible;
- what the competition’s access and publication conditions permit;
- how the source bytes can be acquired and identified reproducibly;
- what one row in each table represents;
- how the tables relate;
- what raw-data quality conditions exist;
- which fields appear available at the intended prediction point;
- which fields must remain quarantined;
- which artifacts may safely be committed publicly.

Stage 1 measures and documents the raw source. It does not clean or transform it for modeling.

## Why this stage exists

A model can be technically correct while answering the wrong question. Before modeling, the project needs evidence for outcome meaning, population limitations, observation timing, table relationships, data quality, leakage risk, reproducibility, and permitted data handling.

Without this stage, a later model might be described as predicting “probability of default” even if the source only supports a narrower, anonymized payment-difficulty label.

## Dependencies inherited from Stage 0

Stage 1 inherits these locked principles:

- The provisional context is unsecured personal lending.
- That framing may be confirmed, narrowed, or rejected by evidence.
- Home Credit does not represent U.S. bank customers, a particular lender, or a production population.
- `TARGET` semantics and prediction horizon are unresolved.
- “LLM explains; deterministic systems decide.”
- The five provenance categories must remain separate.
- The required core must remain locally runnable for `$0`.
- Stage plans must be approved, committed, and pushed before implementation.
- Material deviations require explanation and approval.
- Stage 1 does not satisfy Sacred Gate 1; it provides inputs needed for that later gate.

## Terminology

- **Row grain:** what one row represents, such as one application, prior loan, monthly balance, or payment.
- **Primary key:** a field or field combination expected to identify one row uniquely.
- **Foreign key:** a field used to link a row to another table.
- **Cardinality:** relationship counts, such as one application having many prior-credit records.
- **Orphan:** a child record whose referenced parent cannot be found.
- **Schema:** the expected column names, data types, and structural rules.
- **Missingness:** where and how values are absent.
- **Checksum:** a content fingerprint. SHA-256 verifies whether bytes have changed.
- **Provenance:** evidence of where data came from and how it was handled.
- **Leakage:** information that would not genuinely have been available when the prediction was made.
- **Prediction point:** the assumed moment when model inputs become available.
- **Sentinel:** a special encoded value that may mean unknown or not applicable.
- **Quarantine:** preventing a field from entering modeling until its safety is established.

## Stage scope

### In scope

- Primary-source and terminology research
- Original competition overview, data documentation, source column descriptions, and applicable rules
- `TARGET` event and prediction-horizon assessment
- Allowed and prohibited risk terminology
- Product-scope evidence
- Access and redistribution assessment
- Authorized reproducible acquisition
- Write-once/logically immutable raw snapshots
- SHA-256 manifests
- Complete official file inventory
- Row-grain, key, and relationship analysis
- Raw parseability and schema checks
- Missingness, duplicate, type, domain, and relational checks
- Risk-based prediction-point and leakage assessment
- Synthetic structural fixtures for testing
- Minimal testable data-foundation tooling
- Step explainers, candidate gate, final summary, commit, and push

### Explicitly out of scope

- Feature engineering
- Data cleaning or correction
- Imputation
- Outlier removal
- Train/validation/test splitting
- Model training
- Model evaluation or calibration
- SHAP
- Policy rules
- Regulatory corpus construction
- Synthetic applicant identities or UI workflow fields
- FastAPI
- SQLite or PostgreSQL
- UI work
- LLM or retrieval implementation
- MLflow experiments
- CI or deployment
- Sacred Gate 1 thresholds
- Legal-compliance conclusions

## Product-scope investigation

The neutral `docs/domain/credit-product-scope.md` will assess:

- why unsecured personal lending is the provisional framing;
- which source evidence supports it;
- which evidence limits it;
- whether the source includes products or populations inconsistent with that framing;
- which project claims are allowed;
- which claims remain provisional;
- whether the framing should be confirmed, narrowed, or rejected.

If evidence materially contradicts the current framing, Stage 1 must stop and propose an architecture amendment. It must not silently force the data into the preferred story.

## TARGET investigation

### Evidence hierarchy

Use evidence in this order:

1. Original competition overview and evaluation
2. Original competition data page
3. `HomeCredit_columns_description.csv` from the authorized official bundle
4. Original competition-specific and general rules
5. Original sponsor documentation directly addressing this dataset
6. Competition-host clarifications
7. Secondary discussions only as research leads

A secondary interpretation can reveal a question worth investigating but cannot establish project terminology.

### Questions to resolve

- What event makes `TARGET` equal to 1?
- What makes it equal to 0?
- Does 0 mean successful repayment or merely absence of the defined event?
- Are event thresholds anonymized?
- Is the observation period stated?
- Does the outcome concern the loan associated with the current application?
- Does the source define the observation date?
- Is the outcome censored or incomplete?
- Does the broad competition description overstate what the column definition supports?

### Required output

The target-semantics document must record:

- exact source wording;
- supported interpretation;
- unsupported interpretation;
- known ambiguities;
- prediction-horizon conclusion;
- allowed terminology;
- prohibited terminology;
- consequences for later modeling.

If the event or horizon remains unspecified, that becomes a locked limitation.

Later models would then estimate the probability of `TARGET=1` in the documented historical source context. They would not be described as producing a universal probability of default.

A model output must not be labeled “PD” merely because it is a probability for a credit-related target. If the outcome event or horizon needed for that stronger term is unsupported, using it is prohibited.

## Access, licensing, and publication

Before data acquisition:

- Review original competition-specific and general rules while authenticated.
- Record URLs, access dates, displayed license designation, and relevant restrictions.
- Require the user to accept binding terms personally.
- Confirm whether local educational portfolio use is permitted.
- Determine what may be published, including code, file names, checksums, schemas, column names, aggregate profiles, synthetic fixtures, and copied source descriptions.
- Record uncertain rights explicitly.
- State that the assessment is not legal advice.

### Conservative default until resolved

- Do not commit raw files or archives.
- Do not commit real row samples.
- Do not redistribute the official column-description file.
- Do not copy substantial protected source text.
- Do not assume derived metadata can be published.
- Do not use third-party mirrors to bypass access controls.

If the terms conflict with a public portfolio repository, stop before downloading. Alternatives require separate approval.

## Write-once/logically immutable raw snapshot contract

The Stage 1 raw contract requires:

- Acquisition tooling never modifies raw source files in place.
- Existing snapshot directories are never silently overwritten.
- Each snapshot is identified by manifest metadata and SHA-256.
- Transformations occur under separate derived or artifact paths.
- Validation reads raw files without rewriting them.
- Any checksum mismatch invalidates trust in the snapshot.
- Reacquisition creates a new snapshot identity rather than changing the old record.
- No filesystem-level immutability claim is made.

## Reproducible acquisition

The proposed acquisition path is the official Kaggle CLI.

The acquisition process will:

- require the user’s authenticated Kaggle account;
- never write credentials into project files or output;
- record the competition slug and official source URLs;
- check local disk space;
- download into an ignored temporary raw path;
- preserve the original archive;
- compute archive SHA-256;
- extract to a new snapshot directory;
- reject path traversal and silent overwrite;
- compute file sizes and SHA-256 values;
- record tool and manifest-format versions;
- avoid absolute machine-specific paths in committed metadata;
- verify the snapshot again before relational analysis.

## Expected source inventory

The official inventory to investigate includes:

- `application_train.csv`
- `application_test.csv`
- `bureau.csv`
- `bureau_balance.csv`
- `POS_CASH_balance.csv`
- `credit_card_balance.csv`
- `previous_application.csv`
- `installments_payments.csv`
- `HomeCredit_columns_description.csv`
- `sample_submission.csv`

Every official file will be inventoried even if Stage 2 later excludes it.

## Relational investigation

### Preliminary hypotheses to validate

- `application_train.csv` and `application_test.csv`
  - Expected grain: one current loan application per row
  - Candidate key: `SK_ID_CURR`
  - `TARGET` expected only in training data
- `bureau.csv`
  - Expected grain: one externally reported prior credit
  - Candidate key: `SK_ID_BUREAU`
  - Link through `SK_ID_CURR`
- `bureau_balance.csv`
  - Expected grain: one monthly status observation per externally reported credit
  - Link through `SK_ID_BUREAU`
  - Composite uniqueness must be tested
- `previous_application.csv`
  - Expected grain: one prior Home Credit application
  - Candidate key: `SK_ID_PREV`
  - Link through `SK_ID_CURR`
- `POS_CASH_balance.csv`
  - Expected grain: monthly observations for prior point-of-sale or cash loans
- `credit_card_balance.csv`
  - Expected grain: monthly observations for prior credit cards
- `installments_payments.csv`
  - Expected grain: a payment or missed-payment-related record
  - Multiple rows may legitimately relate to one installment
  - No simple key will be invented without evidence
- `HomeCredit_columns_description.csv`
  - Source evidence, not model input
- `sample_submission.csv`
  - Competition-format support file, not training data

### Documentation required for every table

- Filename
- Source description
- Observed row and column counts
- Row grain
- Candidate key
- Key uniqueness
- Null keys
- Parent and foreign-key relationships
- Cardinality
- Orphan counts and rates
- Time-relative fields
- `TARGET` presence
- Prediction-point availability
- Limitations

## Raw-data validation

### File-level checks

- Expected file presence
- Byte size and SHA-256
- Parseability
- Header presence
- Duplicate headers
- Delimiter and encoding
- Empty or truncated files

### Schema checks

- Column names and counts
- Train/test structure excluding `TARGET`
- Inferred types
- Mixed-type columns
- Missingness
- Schema drift across repeated runs

### Aggregate data checks

- Exact duplicate rows
- Candidate-key duplicates
- Null keys
- `TARGET` values and missingness
- Numeric ranges and quantiles
- Category counts
- Constant or nearly empty columns
- Non-finite numeric values
- Suspicious time values
- Source-documented sentinels

### Relational checks

- Child-to-parent coverage
- Orphan counts
- Relationship cardinalities
- Composite-key candidates
- Train/test application membership
- Cross-table identifier consistency
- Multiplicity distributions

“Impossible” will be used only when supported by authoritative domain or source evidence. Other anomalies will be described as suspicious, undocumented, or unresolved.

## Risk-based leakage assessment

### Table and field-family classification

Classify each table and logical field family first. Relevant families include:

- applicant attributes;
- application-time financial fields;
- prior-credit summaries;
- relative-time fields;
- current-application decisions;
- repayment behavior;
- outcome fields;
- identifiers;
- competition-support fields.

### Column-level review requirements

Column-level review is required for:

- actual Stage 2 candidates;
- plausible future model candidates;
- timing-sensitive fields;
- `TARGET` and proxy candidates;
- fields associated with decisions or outcomes;
- ambiguous or undocumented fields;
- high-risk identifiers;
- fields whose table-level classification is insufficient.

Each reviewed item records:

- table and field;
- field family;
- availability status;
- evidence;
- timing interpretation;
- leakage reasoning;
- Stage 2 eligibility;
- required follow-up.

Allowed statuses are:

- Available at prediction point
- Unavailable at prediction point
- Potentially post-outcome
- Ambiguous
- Unknown

### Safety rule

- Anything not assessed remains quarantined.
- Ambiguous, unknown, or potentially post-outcome fields remain ineligible.
- Absence from the leakage register never implies approval.

This provides complete safety coverage without requiring low-value manual commentary on every unused column.

## Five provenance categories

### Historical source data

- Stored only under ignored raw paths
- Governed by the logical snapshot contract
- Identified through source metadata and checksums

### Engineered model features

- Not created during Stage 1
- Reserved for separate derived paths in Stage 2
- Raw profiles are not features

### Synthetic data

- Synthetic applicant identities and UI fields remain out of scope
- Tiny structural fixtures may be committed for validator tests
- Fixtures must be labeled synthetic and contain no copied source rows
- Fixtures can never enter historical modeling paths

### Fictional internal policy

- Not created during Stage 1
- Must not be inferred from source fields

### Authoritative regulatory material

- No regulatory corpus is created
- Jurisdiction remains open
- Domain descriptions must not be presented as legal conclusions

## Local and committed artifacts

### Local and ignored

- Downloaded archive
- Extracted raw CSVs
- Temporary downloads
- Real row samples
- Detailed profiles containing source values
- DuckDB temporary or spill output
- Logs
- Credentials and authentication state
- Restricted metadata when publication is not permitted

### Committed, subject to the Step 2 publication assessment

- Primary-source register
- `TARGET` and product-scope evidence
- Access and licensing assessment
- Acquisition instructions
- Python source and tests
- `pyproject.toml` and `uv.lock`
- Manifest format and permitted snapshot metadata
- Permitted checksums and file sizes
- Permitted aggregate counts and schema fingerprints
- Relational findings
- Data-quality summary
- Leakage assessment
- Synthetic structural fixtures
- Step explainers and stage summary

If the rules do not clearly permit publishing column-level or aggregate derived metadata, keep it local and commit only a permitted non-sensitive summary plus a checksum of the local report.

## Tool classifications

### Necessary now

- Authoritative source research
- Official authenticated acquisition
- Write-once/logically immutable snapshot behavior
- Memory-efficient, read-only analysis
- SHA-256 manifests
- Testable Python tooling
- Synthetic-fixture unit tests
- Local integration tests against ignored source data
- Dependency locking

### Selected Stage 1 implementation choices

#### uv

- Selected as the Stage 1 environment and dependency manager.
- `pyproject.toml` declares requirements.
- `uv.lock` records exact resolved dependencies.
- uv is necessary for the approved Stage 1 implementation once selected, but it is not permanent system architecture.

#### Official Kaggle CLI

- Selected for competition acquisition.
- It does not accept terms or manage credentials on the user’s behalf.

#### DuckDB

- Recommended and selected for the proposed Stage 1 raw-analysis implementation.
- The architectural requirement is memory-efficient, read-only analysis, not DuckDB.
- It will scan CSV files using explicit in-memory connections and will not create a persistent application database.
- It remains replaceable through the approved deviation process if a controlled benchmark shows it does not meet the requirement.

#### pytest

- Selected for repeatable unit and local integration tests.

#### JSON

- Selected for manifests and machine-readable contracts because Python supports it without another parser dependency.

### Valuable but optional

- Polars as an alternative lazy-processing engine
- Pandas for small metadata tasks or later feature work
- A generated entity-relationship diagram
- Exporting `uv.lock` to a standardized lock format later

### Educational

- SQL relationship checks
- Synthetic malformed fixtures
- Source-claim matrices
- Explicit grain, key, and cardinality documentation

### Premature or overengineered

- Persistent DuckDB, SQLite, or PostgreSQL databases
- FastAPI
- DVC or Git LFS
- Cloud warehouses
- Workflow orchestrators
- Spark
- Great Expectations or another large validation framework
- Feature stores
- Docker
- Restricted-data CI
- MLflow
- Using DuckDB, Polars, and Pandas simultaneously without evidence

## Final six-step implementation order

Each step follows the approved explain → approve → implement → test → verify → explain → document → commit → push cycle.

### Step 1 — Source authority, product scope, and TARGET semantics

#### Authority

This step establishes factual source and terminology evidence. It does not decide data-access or publication policy.

#### Proposed files

- `docs/domain/credit-product-scope.md`
- `docs/data/home-credit-source-assessment.md`
- `docs/data/home-credit-target-semantics.md`
- `docs/data/home-credit-source-register.md`
- `docs/explanations/stage-1/step-1-source-and-target-semantics.md`
- `docs/architecture.md` only if evidence changes, resolves, or materially qualifies an architectural assumption
- `README.md` only for accurate status if needed

#### Verification

- Every substantive claim maps to a primary source.
- Unsupported “default,” “PD,” horizon, jurisdiction, and population claims are absent.
- Secondary sources are not treated as authority.
- Product-scope status is explicit.
- Any architecture update is material, approved, and not merely a dataset finding.

#### What this proves

- Project terminology matches the best available source evidence.
- Ambiguities are explicit.

#### What this does not prove

- Access rights
- Raw schema
- Data quality
- Model validity
- Legal meaning

### Step 2 — Access, licensing, publication, and acquisition contract

#### Authority

This step defines what access and publication are permitted and the behavior acquisition must follow. It does not implement acquisition or download data.

#### Proposed files

- `docs/data/home-credit-access-and-licensing.md`
- `docs/data/home-credit-acquisition-contract.md`
- `data/README.md`
- `data/raw/README.md`
- `.gitignore` only if the approved contract introduces an unprotected local path
- `docs/explanations/stage-1/step-2-access-and-acquisition-contract.md`

#### Verification

- Official rules and source URLs are recorded with access dates.
- User-controlled terms acceptance is explicit.
- Allowed, prohibited, and uncertain publication categories are separated.
- No credential or authenticated response is committed.
- Raw storage and logical snapshot rules are unambiguous.
- Step 3 acceptance criteria are defined.

#### What this proves

- Step 3 has an approved contract to implement.

#### What this does not prove

- That authentication works
- That data has been acquired
- That legal advice has been provided
- That every future use is permitted

### Step 3 — Minimal tooling and authorized acquisition

#### Authority

This step implements the Step 2 contract, performs authorized acquisition, and produces the verified local raw snapshot and manifest.

#### Proposed files

- `pyproject.toml`
- `uv.lock`
- `.python-version`
- `src/credit_underwriting/__init__.py`
- `src/credit_underwriting/data/__init__.py`
- `src/credit_underwriting/data/acquisition.py`
- `src/credit_underwriting/data/manifest.py`
- `tests/data/test_acquisition.py`
- `tests/data/test_manifest.py`
- `data/manifests/home-credit-default-risk.json`
- `docs/explanations/stage-1/step-3-raw-snapshot-and-manifest.md`

#### Local ignored directories

- `data/raw/home-credit-default-risk/downloads/`
- `data/raw/home-credit-default-risk/snapshots/<snapshot-id>/`

#### Verification

- `uv sync` succeeds from the committed lockfile.
- Unit tests use synthetic archives and temporary directories.
- Unsafe archive paths and silent overwrite are rejected.
- SHA-256 recomputation matches the manifest.
- The official file inventory reconciles with the acquired bundle.
- Raw bytes are not tracked by Git.
- Existing raw files remain unchanged during validation.

#### What this proves

- The exact local source snapshot is identifiable and re-verifiable.
- Acquisition behavior follows the approved contract.

#### What this does not prove

- Semantic correctness
- Relational integrity
- Data quality
- Rights beyond the reviewed contract
- Continued future source availability

### Step 4 — Table inventory and relational contracts

#### Proposed files

- `data/contracts/home-credit/table-contracts.json`
- `docs/data/home-credit-table-inventory.md`
- `docs/data/home-credit-relational-model.md`
- `src/credit_underwriting/data/inventory.py`
- `tests/data/test_inventory.py`
- `tests/fixtures/synthetic/home-credit-structure/`
- `tests/fixtures/synthetic/home-credit-structure/README.md`
- `docs/explanations/stage-1/step-4-table-and-relational-contracts.md`

#### Publication condition

Column-level contracts are committed only if Step 2 permits them. Otherwise, the detailed contract remains local and Git stores a permitted summary and report checksum.

#### Verification

- Synthetic fixtures prove key, duplicate, and orphan detection.
- Local integration checks scan the authorized snapshot.
- Every official file has a documented purpose.
- Candidate keys are tested rather than assumed.
- Relationships account for train and test application membership where relevant.
- Counts reconcile with the manifest.

#### What this proves

- The acquired snapshot’s observed grains, keys, and relationships are documented.

#### What this does not prove

- Business correctness of every row
- Feature eligibility
- Future snapshot stability
- Modeling split validity

### Step 5 — Raw-data quality baseline

#### Proposed files

- `src/credit_underwriting/data/validation.py`
- `tests/data/test_validation.py`
- `docs/data/home-credit-quality-baseline.md`
- `data/manifests/home-credit-default-risk.json`, updated with permitted aggregate metadata
- `.gitignore`, updated to protect `artifacts/data-profiles/`
- `docs/explanations/stage-1/step-5-raw-data-quality-baseline.md`

#### Local ignored directory

- `artifacts/data-profiles/home-credit/<snapshot-id>/`

#### Verification

- Valid and intentionally malformed synthetic fixtures are tested.
- All source tables pass or produce documented parseability findings.
- Missingness, duplicates, key failures, type issues, suspicious domains, and relationship findings are reproducible.
- Repeated runs produce stable aggregate results.
- No real rows or restricted profiles are tracked.
- Raw checksums remain unchanged.

#### What this proves

- Raw quality conditions in this snapshot are measured and reproducible.

#### What this does not prove

- Anomaly treatment
- Representativeness
- Model suitability
- Random missingness
- Fairness
- Causal meaning

### Step 6 — Risk-based leakage and provenance controls

#### Proposed files

- `docs/data/home-credit-leakage-assessment.md`
- `docs/data/provenance-boundaries.md`
- `data/contracts/home-credit/leakage-register.csv` if Step 2 permits publication
- `tests/data/test_leakage_register.py` if a machine-readable register is committed
- `docs/explanations/stage-1/step-6-leakage-and-provenance-controls.md`
- `docs/architecture.md` only if evidence changes, resolves, or materially qualifies architecture
- `README.md` for accurate stage status at closeout

#### Verification

- Every table and logical field family has a risk classification.
- Every actual or potential modeling candidate has column-level review.
- Timing-sensitive, target/proxy, ambiguous, and high-risk fields receive column-level review.
- Unassessed fields remain quarantined.
- Absence from the register never implies approval.
- Synthetic fixtures remain separate.
- No fictional policy or regulatory corpus appears.
- Terminology matches the `TARGET` evidence.
- Architecture contains only architectural conclusions, not general findings.

#### What this proves

- Stage 2 has a controlled eligibility and quarantine boundary.

#### What this does not prove

- Future engineered features are leakage-free
- A modeling split is valid
- Every timing ambiguity is resolved
- A feature is useful, fair, or causal

## Stage closeout

After Step 6:

- Run the candidate Stage 1 gate.
- Create `docs/explanations/stage-1/stage-1-summary.md` from actual results.
- Record approved deviations and unresolved limitations.
- Run final verification including the summary.
- Commit and push the summary and any final documentation changes.
- Confirm local `main`, upstream, and GitHub `main` agree.
- Confirm a clean working tree.

## Final proposed file set

### Planning artifact

- `docs/plans/stage-1-plan.md`

### Domain and evidence documents

- `docs/domain/credit-product-scope.md`
- `docs/data/home-credit-source-assessment.md`
- `docs/data/home-credit-target-semantics.md`
- `docs/data/home-credit-source-register.md`
- `docs/data/home-credit-access-and-licensing.md`
- `docs/data/home-credit-acquisition-contract.md`
- `docs/data/home-credit-table-inventory.md`
- `docs/data/home-credit-relational-model.md`
- `docs/data/home-credit-quality-baseline.md`
- `docs/data/home-credit-leakage-assessment.md`
- `docs/data/provenance-boundaries.md`
- `data/README.md`
- `data/raw/README.md`

### Python environment and source

- `pyproject.toml`
- `uv.lock`
- `.python-version`
- `src/credit_underwriting/__init__.py`
- `src/credit_underwriting/data/__init__.py`
- `src/credit_underwriting/data/acquisition.py`
- `src/credit_underwriting/data/manifest.py`
- `src/credit_underwriting/data/inventory.py`
- `src/credit_underwriting/data/validation.py`

### Machine-readable metadata

- `data/manifests/home-credit-default-risk.json`
- `data/contracts/home-credit/table-contracts.json` if publication is permitted
- `data/contracts/home-credit/leakage-register.csv` if publication is permitted

### Tests and fixtures

- `tests/data/test_acquisition.py`
- `tests/data/test_manifest.py`
- `tests/data/test_inventory.py`
- `tests/data/test_validation.py`
- `tests/data/test_leakage_register.py` when applicable
- `tests/fixtures/synthetic/home-credit-structure/`
- `tests/fixtures/synthetic/home-credit-structure/README.md`

### Explanations

- `docs/explanations/stage-1/step-1-source-and-target-semantics.md`
- `docs/explanations/stage-1/step-2-access-and-acquisition-contract.md`
- `docs/explanations/stage-1/step-3-raw-snapshot-and-manifest.md`
- `docs/explanations/stage-1/step-4-table-and-relational-contracts.md`
- `docs/explanations/stage-1/step-5-raw-data-quality-baseline.md`
- `docs/explanations/stage-1/step-6-leakage-and-provenance-controls.md`
- `docs/explanations/stage-1/stage-1-summary.md`

### Conditional current-state updates

- `docs/architecture.md` only for material architectural conclusions
- `README.md` for accurate current status
- `.gitignore` only for approved local artifact paths

## Stage 1 completion gate

Stage 1 passes only when:

- The final approved Stage 1 plan was committed and pushed before implementation.
- All six implementation steps completed their normal approval-through-push cycle.
- Product-scope status is evidence-backed.
- `TARGET`’s supported meaning is documented.
- Prediction-horizon status is explicit, including if unknowable.
- Allowed and prohibited terminology is documented.
- Every substantive source claim is traceable.
- Original competition rules and access conditions were reviewed.
- Publication handling is documented.
- No credentials or prohibited content are tracked.
- Acquisition occurred only after authorization.
- The raw snapshot obeys the write-once/logically immutable contract.
- Archive and file checksums are reproducible.
- A checksum mismatch invalidates snapshot trust.
- Every official file is inventoried.
- Row grains and candidate keys are documented.
- Key uniqueness, null-key, orphan, and cardinality checks ran.
- Parseability, schema, type, missingness, duplicate, suspicious-value, and relational findings are recorded.
- Raw files were not modified during analysis.
- Tables and logical field families have leakage-risk classification.
- Actual and potential modeling candidates received column-level review.
- Unassessed and unresolved fields remain quarantined.
- Absence from the leakage register never implies approval.
- Synthetic fixtures are labeled and isolated.
- Unit tests pass using synthetic fixtures.
- Local integration checks pass against the authorized snapshot or produce explicitly approved documented failures.
- Tests state what they prove and do not prove.
- No application, feature, model, policy, database, API, UI, or LLM work entered scope.
- All six step explainers exist.
- Candidate verification ran before the retrospective summary.
- The stage summary records actual evidence and deviations.
- Final scope, documentation, secret, Git-ignore, diff, Git, remote, and clean-working-tree checks pass.

Downloading files alone does not satisfy the gate.

A licensing or access blocker prevents Stage 1 completion unless the user approves a revised source strategy.

## Decisions locked if Stage 1 passes

Subject to actual evidence:

- Authoritative source hierarchy
- Product-scope conclusion and its remaining limitations
- Exact official snapshot identity
- Supported `TARGET` interpretation
- Any irreducible `TARGET` or horizon ambiguity
- Allowed and prohibited model terminology
- Reviewed access and publication contract
- Official-source-only acquisition
- Write-once/logically immutable raw snapshot behavior
- SHA-256 manifest format
- Observed file inventory
- Observed table grains
- Validated key and relationship findings
- Known raw-quality limitations
- Table and field-family leakage classifications
- Column-level decisions for reviewed candidates and high-risk fields
- Quarantine by default for unassessed fields
- Separation of historical data from synthetic fixtures
- uv as the Stage 1 environment-management implementation
- The selected Stage 1 raw-analysis implementation, without making it permanent architecture

Locked findings may change only through new evidence and the approved deviation process.

## Decisions remaining open

### For Stage 1

- Exact Python version, until local compatibility and dependency support are checked
- Whether the rules permit public column-level contracts or leakage registers
- Whether DuckDB remains suitable after a small controlled benchmark
- Whether `docs/architecture.md` needs any Stage 1 update

### For Stage 2 and later

- Train/validation/test split
- Modeling cohort
- Table inclusion
- Missing-value treatment
- Outlier or sentinel treatment
- Aggregation windows
- Feature definitions
- Categorical encoding
- Numerical transformations
- Model family
- Metrics and thresholds
- Calibration method
- Fairness metrics
- Protected-attribute handling
- Policy and regulatory design
- Persistence, API, UI, LLM, retrieval, and deployment choices

## What Stage 2 may safely assume

After Stage 1 passes:

- The source snapshot is identified by verified checksums.
- Authorized acquisition instructions exist.
- Raw data is not tracked by Git.
- The snapshot is write-once/logically immutable under project tooling.
- `TARGET` terminology and horizon limitations are documented.
- Product framing has an evidence-backed status.
- Every official file has a documented role.
- Row grains and observed relationships are available.
- Raw quality issues are measured but not silently corrected.
- Table and field-family leakage risks are documented.
- Reviewed candidates have eligibility decisions.
- Everything else remains quarantined.
- Synthetic fixtures cannot be confused with historical source data.
- Memory-efficient, read-only validation tooling exists.
- Stage 2 still needs an approved plan before selecting splits, transformations, aggregations, or features.

## Risks and likely revision points

- Competition rules may restrict the intended public-repository artifacts.
- Authentication may require user action.
- `TARGET` thresholds or horizons may remain anonymized.
- “Probability of `TARGET=1`” may be the strongest supportable model language.
- Source products may not align cleanly with unsecured personal lending.
- Some tables may lack simple primary keys.
- Apparent duplicates may be legitimate under the true row grain.
- Supporting tables may not join cleanly to training applications alone.
- Relative-time fields may be difficult to align to the prediction point.
- Extreme values may be valid sentinels.
- Publishing column-level derived metadata may be restricted.
- The data volume may exceed available memory or disk expectations.
- DuckDB may require configuration or replacement after a controlled benchmark.
- Kaggle may change packaging or access behavior.
- Original documentation may remain insufficient to resolve a business-semantic question.

Any material conflict discovered during implementation triggers the approved deviation process rather than silent reconciliation.

## Deviation process

Once implementation begins, preserve this plan’s original intended decisions. If a material deviation becomes necessary:

1. Explain the approved decision and discovered problem.
2. Present the proposed change, alternatives, benefits, and costs.
3. Wait for explicit approval.
4. Preserve the original plan text.
5. Record the deviation in the relevant step explainer.
6. Record it in the final Stage 1 summary.
7. Append a clearly labeled approved amendment to this plan when useful.
8. Update `docs/architecture.md` only when current architectural truth genuinely changes.
9. Verify, commit, and push the approved change through the normal workflow.

## Stage closeout sequence

1. Complete all six approved steps and their individual commits and pushes.
2. Run the candidate Stage 1 gate.
3. Create the retrospective `docs/explanations/stage-1/stage-1-summary.md` from actual evidence.
4. Run final verification with the summary included.
5. Commit and push the closeout documentation.
6. Confirm local `main`, upstream `main`, and GitHub `main` agree.
7. Confirm the working tree is clean.
8. Report what was proven, what was not proven, remaining limitations, and what Stage 2 may safely assume.
