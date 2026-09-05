# Stage 1 Step 1 — Source Authority, Product Scope, and TARGET Semantics

## 1. What this step does

This step establishes a traceable evidence foundation for the Home Credit competition's provenance, the project's provisional credit-product framing, and the permitted interpretation of `TARGET`.

It creates documentation only. It does not acquire data, decide licensing, create a Python environment, or implement analytical or application behavior.

## 2. Why this step exists

A model can perform well while its output is described incorrectly. Before later stages select features or train a model, the project must know which claims come directly from the source, which are inferences, and which remain unknown.

This step prevents the competition title, common community terminology, or a preferred product story from silently becoming a stronger business definition than the evidence supports.

## 3. What existed before

Stage 0 had established:

- unsecured personal lending as a provisional product context;
- Home Credit `TARGET` meaning and horizon as open decisions;
- strict population and provenance boundaries;
- the rule that unsupported default and horizon claims are prohibited;
- the approved explain-through-push workflow.

The approved Stage 1 plan was committed and pushed as `18051dd`. No Stage 1 evidence documents or implementation existed.

## 4. What exists afterward

The repository now has:

- a canonical register of authoritative, deferred, lead-only, and rejected sources;
- a source-provenance and population assessment;
- a conservative target and horizon assessment;
- an evidence-backed product-scope status;
- claim-level mappings from conclusions to specific source IDs;
- an explicit boundary between Step 1 evidence and Step 2 licensing work.

Exact `TARGET` semantics and horizon remain unresolved. That is an evidence result, not an omitted conclusion.

## 5. Files created or modified

Created:

- `docs/domain/credit-product-scope.md`
- `docs/data/home-credit-source-assessment.md`
- `docs/data/home-credit-target-semantics.md`
- `docs/data/home-credit-source-register.md`
- `docs/explanations/stage-1/step-1-source-and-target-semantics.md`

Not modified:

- `docs/plans/stage-1-plan.md`
- `docs/architecture.md`
- `README.md`
- all Stage 0 artifacts

No dataset, environment, source-code, model, API, database, UI, or LLM file was created.

## 6. Architecture and data-flow walkthrough

Step 1 establishes a documentation evidence flow:

```text
original competition and sponsor sources
  → canonical source IDs and authority classification
  → claim-level provenance and qualifications
  → target-language constraints and product-scope status
  → inherited boundaries for later Stage 1 steps
```

The source register owns source identity. The source assessment owns provenance and population findings. The target document owns `TARGET` and horizon language. The domain document owns product framing. This explainer records execution history.

`docs/architecture.md` remains authoritative for current architecture. The evidence left its provisional product and open target decisions unchanged, so no amendment was needed.

## 7. Important implementation explained

The original Kaggle overview, evaluation, data page, and rules were inspected directly. Home Credit Group's official 2018 annual report supplied period-relevant corporate context.

The public competition pages establish a broad repayment-prediction task, identify `TARGET` as the submission field, and describe the main table and supporting histories. They do not expose the field-level target rule or an outcome horizon.

The official `HomeCredit_columns_description.csv` preview required sign-in and competition-rules acceptance. It was not downloaded. A participant write-up that attributes a definition to that file was registered only as a secondary lead. Its wording was not adopted as authoritative evidence.

The resulting target decision is deliberately narrow:

- `TARGET=1` is an unresolved source label;
- `TARGET=0` has no independently verified business meaning;
- the horizon is unresolved;
- default, probability of default, and PD remain prohibited;
- successful-repayment language for `TARGET=0` remains prohibited.

The product decision is “Remains provisional.” Official sources support a broad consumer-finance loan context but do not establish the current applications as unsecured personal loans or provide a stronger dataset-specific replacement scope.

## 8. New concepts introduced

- **Claim-level traceability:** assigning evidence to one specific conclusion rather than placing a citation near several claims.
- **Direct source statement:** a claim explicitly made by an authoritative source.
- **Supported inference:** a narrow conclusion reasoned from cited facts but not stated verbatim.
- **Unresolved ambiguity:** a question the inspected evidence cannot answer reliably.
- **Complementary class:** records not assigned to a defined positive class; this does not automatically mean successful repayment.
- **Prediction horizon:** the future period over which an outcome is measured.
- **Population transfer:** applying findings from one source population to another; this requires evidence rather than assumption.

## 9. Design decisions

- Use stable source IDs as the single source-identity system.
- Put claim mappings inside the three evidence documents rather than create a citation database.
- Treat broad competition language as context, not a field definition.
- Treat corporate documentation as sponsor-related context, not dataset composition.
- Record inaccessible authoritative evidence as deferred.
- Preserve unresolved conclusions when stronger language is not justified.
- Leave product scope provisional instead of forcing confirmation or premature reframing.
- Keep Step 2 licensing authority out of Step 1.

## 10. Why this approach

The approach preserves a reviewable chain from each conclusion to the source that supports it. It also makes missing evidence visible. That is safer than allowing the competition title, secondary explanations, or group-wide business facts to stand in for dataset-specific documentation.

Keeping the documents specialized reduces duplication and lets later stages update current evidence without rewriting this historical explainer.

## 11. Alternatives considered

- Adopt the target definition reproduced in a participant write-up.
- Obtain the column-description file from a public mirror.
- Treat the competition title as proof of a default target.
- Infer that `TARGET=0` means successful repayment.
- Infer a horizon from installment language in secondary material.
- Confirm unsecured personal lending from Home Credit's broad business context.
- Reframe the product immediately to generic consumer credit.
- Duplicate source metadata in every evidence document.

## 12. Why alternatives were rejected or deferred

Participant material is not authoritative. A mirror would bypass the approved acquisition boundary and weaken provenance. Titles and broad narratives do not define field coding. A negative class cannot be translated into successful repayment without source support. The horizon cannot be guessed.

Home Credit's annual report describes a broad group portfolio, not the competition sample. That evidence is too broad both to confirm unsecured personal lending and to impose a precise replacement product scope.

Duplicating source metadata would create drift; stable source IDs provide cleaner traceability.

## 13. Tests written

No application tests were written because Step 1 is documentation-only.

Repeatable documentation checks covered:

- expected file scope;
- approved-plan immutability;
- unique and resolvable source IDs;
- claim-mapping completeness;
- product-status cardinality;
- target and horizon status;
- prohibited terminology controls;
- population limitations;
- Step 2 authority boundary;
- deferred official artifact handling;
- relative-link targets;
- whitespace and end-of-file formatting;
- common secret patterns;
- absence of dataset and implementation files.

Manual evidence review checked whether assigned sources support the specific claims mapped to them.

## 14. What the tests prove

The checks prove that:

- all four evidence documents existed before this explainer was written;
- the approved plan's working-tree blob matched its committed blob;
- source IDs were unique and every referenced ID resolved;
- the product, source, and target documents contained complete claim mappings;
- exactly one current product status was selected;
- `TARGET=1`, `TARGET=0`, and horizon limitations were explicit;
- stronger `TARGET=0`, default, and PD language was prohibited;
- repository-relative file links targeted existing files;
- the checked files contained no detected whitespace or common-secret issue;
- no dataset, Python-environment, or implementation artifact existed.

## 15. What the tests do not prove

The checks do not prove:

- the contents of the deferred official column-description file;
- exact target semantics or horizon;
- dataset access, use, licensing, or publication rights;
- actual raw-file schema, row grain, quality, or relationships;
- the source sample's country, operating entity, dates, or representativeness;
- that unsecured personal lending will remain the final product framing;
- model accuracy, calibration, fairness, compliance, or production suitability.

## 16. Verification results

Candidate verification passed across the four evidence documents before this explainer was created.

Observed results included:

- approved Stage 1 plan blob unchanged: `80844d68c1175f90fc8ed94918499b0f404faa05`;
- four expected evidence documents and no other working-tree files;
- unique source-register IDs;
- every referenced source ID resolved;
- seven fully mapped product-scope claims;
- eight fully mapped source-assessment claims;
- seven fully mapped target-semantics claims;
- exactly one product status: “Remains provisional”;
- explicit unresolved statuses for `TARGET=1`, `TARGET=0` business meaning, and horizon;
- explicit prohibition of unsupported default, PD, and successful-repayment interpretations;
- valid repository-relative file targets;
- no block quotations or substantial source reproduction;
- clean whitespace after formatting correction;
- no detected common secret pattern;
- no dataset, Python environment, or implementation files.

Final verification is rerun with this explainer included before commit.

## 17. Problems encountered

The most important evidence blocker was that the official field-description preview required sign-in and acceptance of competition rules. The accessible public competition pages did not define the target event or horizon.

Search results exposed participant-authored reproductions of an alleged target definition, creating a risk that familiar wording could be mistaken for primary evidence.

The first candidate status check used Git's directory-collapsing display and expected individual untracked paths. Two later assertions were initially too literal about capitalization or Markdown punctuation. These were verification-command issues, not document failures.

Initial drafts also had extra blank lines at end of file.

## 18. How problems were solved

The inaccessible official artifact was registered as deferred to authorized acquisition. The participant write-up was registered as a lead only and excluded from substantive conclusions.

The target and product documents preserve unresolved statuses instead of guessing. Verification was rerun with individual untracked-file enumeration and checks that matched the documents' actual Markdown representation.

Trailing blank lines were removed without changing evidence or conclusions.

## 19. Interview questions and strong answers

### Why did you leave the target unresolved when a definition is widely repeated online?

Because the project requires authoritative provenance. The accessible official pages did not contain the field rule, and the official artifact was access-gated. A participant's quotation is useful as a lead, but adopting it as fact would make the evidence chain weaker than the claim.

### Why is `TARGET=0` not called successful repayment?

A negative binary class may only mean that the positive labeling condition was not observed. It does not automatically prove complete or timely repayment. The stronger interpretation requires an authoritative business definition.

### Why is the product scope still provisional?

The evidence supports loans in a broad consumer-finance context, but it does not identify the current applications as exclusively unsecured personal loans. It also does not provide a precise dataset-specific replacement scope.

## 20. Hard or senior-level interview questions

### How do you prevent a citation from laundering several unsupported claims?

Each material conclusion has its own classification, source IDs, and qualification. Review checks whether those exact sources support that exact claim. Proximity within a paragraph is not treated as evidence.

### When should broad corporate evidence be applied to a dataset?

Only when a dataset-specific source establishes the connection. Corporate reports can explain the sponsor's business context, but group-wide countries, products, collateral, or risk definitions cannot be assigned to anonymized competition rows by assumption.

### Does an unresolved target block all progress?

It blocks stronger model claims, not evidence collection. Later authorized source inspection may resolve it. If ambiguity remains, the project can still model the source label only if later stages design evaluation and communication around that limitation.

## 21. What comes next and why

After final verification, this focused documentation step is committed and pushed. Stage 1 Step 2 may then be proposed through the normal explain-before-implementation workflow.

Step 2 must define access, licensing, publication, and acquisition behavior before any dataset download. It inherits the deferred official column-description artifact, the unresolved target and horizon, the provisional product scope, and the prohibition on using unofficial mirrors.
