# Stage 1 Step 2 — Access, Licensing, Publication, and Acquisition Contract

## 1. What this step does

This step evaluates the authoritative conditions governing Home Credit competition data and defines the safety contract a future acquisition implementation would have to satisfy.

It separates project handling from legal-rights claims and records one current Step 3 readiness status. It does not acquire data, authenticate, accept terms, or implement acquisition code.

## 2. Why this step exists

The ability to download a file is not permission to use it for every purpose or publish it. A public portfolio adds a further audience beyond the person who accepted source terms.

Step 2 prevents technical convenience from silently becoming a rights conclusion. It also lets later implementation inherit precise identity, checksum, extraction, and no-overwrite behavior if an approved source strategy becomes compatible.

## 3. What existed before

Stage 1 Step 1 had established:

- the original competition and sponsor provenance;
- a broad historical loan-repayment task context;
- unresolved `TARGET=1`, `TARGET=0` business meaning, and prediction horizon;
- “Remains provisional” as the product-scope status;
- the official column-description artifact as access-gated and deferred;
- no conclusion about access, use, licensing, or publication.

The repository was clean on `main` at commit `bbb6d5b479c6160accc0e2f027e64e3cd527cf33`.

## 4. What exists afterward

The repository now has:

- a source-specific access, use, and publication assessment;
- intended-use classifications that do not convert silence into permission;
- individual handling classifications for all approved artifact categories;
- an explicit user-controlled acceptance boundary;
- a technical acquisition contract separating event identity from content identity;
- a concise data-area map and raw-path safety guide;
- a blocked readiness conclusion that prevents Step 3 from starting.

No data implementation exists afterward.

## 5. Files created or modified

Created:

- `docs/data/home-credit-access-and-licensing.md`
- `docs/data/home-credit-acquisition-contract.md`
- `data/README.md`
- `data/raw/README.md`
- `docs/explanations/stage-1/step-2-access-and-acquisition-contract.md`

Not modified:

- `.gitignore`
- `docs/plans/stage-1-plan.md`
- all Step 1 evidence and the Step 1 explainer
- `docs/architecture.md`
- `README.md`

No dataset, archive, real row, credential, environment, Python file, manifest, or acquisition implementation was created.

## 6. Architecture and data-flow walkthrough

The governance flow is:

```text
authoritative competition and platform terms
  → intended-use evidence status
  → artifact project-handling classification
  → Step 3 readiness status
  → technical acquisition contract, only if later ready and user-authorized
```

The access assessment owns terms and project handling. The acquisition contract owns deterministic Step 3 behavior. The two data READMEs provide concise operational guidance. This explainer records what actually happened.

The current result does not change system architecture. It blocks the planned Home Credit acquisition path pending a separately approved source strategy.

## 7. Important implementation explained

The publicly accessible competition rules contain a specific data-use provision that replaces the broader general competition rule. The specific provision limits Home Credit Competition Data use to competition purposes.

The same rules restrict publishing or redistributing Competition Data to non-participants. The public data page labels the bundle “Subject to Competition Rules” and requires sign-in or registration plus rules agreement before file access.

The current Kaggle Terms of Use, effective 2025-06-22, establish current platform-level content conditions but do not expand the narrower competition provision.

Because this project is a public educational portfolio rather than participation in the closed 2018 competition, the access assessment records `Blocked — incompatible conditions`. That is a project-readiness conclusion, not a legal opinion about every hypothetical use.

The acquisition contract remains useful as a safety specification. It gives each attempt a random Acquisition ID while deriving snapshot/content identity only from normalized extracted paths, sizes, and full file SHA-256 values. Identical logical content therefore retains one deterministic content identity even across repeated acquisition events or repackaged archives.

## 8. New concepts introduced

- **Permission dimension:** one specific question—such as access or redistribution—that must not be answered by evidence about another question.
- **Project-handling classification:** the repository's approved treatment of an artifact, not a broad declaration of legal rights.
- **Acquisition ID:** a unique identifier for one download attempt.
- **Snapshot/content ID:** a deterministic identifier for normalized extracted content.
- **Canonical serialization:** one precisely defined byte representation so identical logical metadata hashes identically.
- **Fail closed:** refuse to proceed when integrity or permission evidence is missing or contradictory.
- **Path traversal:** an archive path designed to escape its intended extraction directory.

## 9. Design decisions

- Give competition-specific restrictions precedence where the source expressly says they replace a general provision.
- Record project-purpose incompatibility instead of treating non-commercial intent as permission.
- Keep all unresolved source-derived metadata local-only.
- Permit only independently generated synthetic material and source-agnostic original code under separate project conditions.
- Separate Acquisition ID from snapshot/content ID.
- Exclude timestamps, account data, tool version, and archive packaging from logical content identity.
- Keep full archive and file SHA-256 values as integrity evidence.
- Preserve the contract even though current readiness is blocked.
- Leave `.gitignore` unchanged because existing rules already protect the approved project-local raw paths.

## 10. Why this approach

This approach follows the most specific available source condition and avoids manufacturing permission from broad terms or silence. It keeps the public repository safe while making the blocker explicit and reviewable.

The two-identity design also avoids falsely versioning byte-identical extracted content merely because it was downloaded twice. At the same time, each download remains independently auditable.

## 11. Alternatives considered

- Rely on the general rule's mention of academic or educational use.
- Treat a non-commercial portfolio as a competition purpose.
- Accept the rules or authenticate on the user's behalf.
- Download first and decide publication later.
- Publish only small row samples.
- Assume checksums and aggregate metadata are automatically safe to publish.
- Use an unofficial mirror for the column-description file.
- Include acquisition time in snapshot identity.
- Include archive SHA-256 in logical content identity.
- Modify `.gitignore` despite existing coverage.

## 12. Why alternatives were rejected or deferred

The Home Credit-specific provision expressly replaces the broader general data-use clause. Calling portfolio work a competition purpose would be unsupported interpretation.

Binding account actions belong to the user. Downloading before resolving purpose would violate the approved workflow. Small samples remain source data, and the reviewed terms do not expressly classify derived metadata.

A mirror would bypass the official access boundary. Timestamps would make identical content appear different. Archive hashes are retained separately so repackaging alone does not change logical extracted-content identity.

Changing `.gitignore` would add noise without increasing protection because `data/raw/*` already covers the complete proposed layout while allowing the tracked raw README.

## 13. Tests written

No application tests were written because Step 2 is documentation and contract design only.

Candidate documentation checks covered:

- exact file scope;
- immutable approved plan and Step 1 evidence;
- authoritative term metadata;
- intended-use vocabulary;
- artifact classification completeness;
- evidence or policy reasons for restrictive handling;
- distinct permission dimensions;
- user-controlled acceptance wording;
- Acquisition ID and snapshot/content ID separation;
- deterministic identity inputs and serialization;
- secure extraction and no-overwrite rules;
- `.gitignore` behavior for representative future raw paths;
- repository-relative links;
- whitespace and common secret patterns;
- absence of datasets and implementation artifacts.

Manual review checked the public competition rules, data page, current Kaggle terms, and official Kaggle API and CLI documentation.

## 14. What the tests prove

The checks prove that:

- only the four candidate current-state documents existed before this explainer;
- the Stage 1 plan, Step 1 evidence, architecture, README, and `.gitignore` retained their original Git blobs;
- six authoritative sources have traceable metadata;
- seven intended uses have one approved evidence status each;
- all seventeen required artifact categories have one current handling classification each;
- unresolved derived metadata remains local-only;
- the contract contains the approved deterministic identity and safety requirements;
- proposed archive and snapshot files are ignored while `data/raw/README.md` remains trackable;
- repository-relative links resolve;
- no dataset or Step 3 artifact was present.

## 15. What the tests do not prove

The checks do not prove:

- legal advice or legal certification;
- the enforceability of any term;
- the exact historical version of Kaggle terms incorporated in 2018;
- account-specific terms or authenticated access behavior;
- that the user accepted any term;
- that authentication or acquisition works;
- the content or treatment of an uninspected authenticated prompt;
- that source-derived metadata may be published;
- archive safety, completeness, or integrity;
- actual content-ID implementation behavior;
- any data, model, fairness, or production property.

## 16. Verification results

Candidate verification passed for the four current-state Step 2 documents before this explainer was created.

Observed candidate results:

- exactly four expected untracked files;
- clean `git diff --check` output;
- approved Stage 1 plan blob unchanged: `80844d68c1175f90fc8ed94918499b0f404faa05`;
- all five Step 1 document blobs unchanged;
- architecture, README, and `.gitignore` blobs unchanged;
- six complete `HC-TERM` source records;
- seven intended-use evidence statuses using the approved vocabulary;
- seventeen artifact handling classifications;
- all checked repository-relative links resolved;
- representative acquisition archive and snapshot files matched `.gitignore` rule `data/raw/*`;
- `data/raw/README.md` matched the tracked exception;
- no detected credential assignment or secret value;
- no dataset, environment, or acquisition implementation file.

Final verification then passed with this explainer included. It confirmed:

- exactly the five approved Step 2 deliverables and no `.gitignore` change;
- all 21 required explainer sections in order;
- the same protected-file hashes recorded at the candidate gate;
- six sources, seven intended uses, and seventeen artifact classifications;
- all six permission dimensions;
- one selected readiness status in the authoritative access document;
- resolved relative links and clean whitespace;
- representative raw paths ignored and the raw README trackable;
- no detected credential value, block quotation, dataset, archive, environment, manifest, or acquisition code.

## 17. Problems encountered

The key source conflict was substantive rather than technical: the general competition rule mentions broader educational and non-commercial uses, but the Home Credit-specific provision replaces it with a competition-only purpose.

The rules page does not show a revision history or effective date for its current text. The current Kaggle terms are dated 2025, years after the competition. Complete file content and any account-specific prompt remain authentication-gated.

Derived metadata such as checksums, schemas, and aggregate findings is not expressly classified by the reviewed sources.

## 18. How problems were solved

The source-specific provision controlled the project assessment because it expressly supersedes the general clause. The project recorded an incompatible readiness status rather than inventing a portfolio exception.

Historical-version and authenticated-view questions remain documented limitations. They were not filled with secondary commentary or an unauthorized login.

Unresolved derived metadata was assigned local-only handling. No data was acquired merely to make the classification question more concrete.

## 19. Interview questions and strong answers

### Why does non-commercial intent not settle this question?

Because the source-specific rule states a narrower allowed purpose than the general non-commercial language. Permission must follow the applicable specific condition, not the project's preferred characterization.

### Why keep an acquisition contract when acquisition is blocked?

The safety requirements remain reusable if authoritative permission is later obtained or a compatible source is approved. Keeping readiness separate from implementation prevents the contract from being mistaken for authorization.

### Why are checksums local-only?

They are derived from restricted source bytes, and the reviewed terms do not expressly address publishing them. The project therefore treats the uncertainty conservatively.

## 20. Hard or senior-level interview questions

### Why is archive SHA-256 excluded from logical snapshot identity?

Archive containers can change compression or packaging while extracting to identical files. File paths, sizes, and hashes identify the logical payload; the archive hash remains separate evidence about the exact downloaded container.

### How does the design avoid time-based false versions?

Acquisition time belongs only to the event record. The content ID hashes a canonical inventory that excludes time, event ID, account, machine path, and tool version.

### Does a blocked status mean the project has made a final legal determination?

No. It means the approved project purpose is incompatible with the narrow authoritative condition currently documented, so the engineering workflow refuses acquisition. Broader legal conclusions are outside this project.

## 21. What comes next and why

Step 3 does not begin.

The next action requires a separately explained and approved source-strategy decision. Options include obtaining authoritative permission for the intended use, selecting a compatible alternative dataset, or revising the data strategy toward independently generated synthetic material.

Any resulting material change to current architecture or the approved Stage 1 plan must follow the deviation process before implementation.
