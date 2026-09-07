# Home Credit Access, Use, and Publication Assessment

## Purpose and authority

This document is authoritative for the project's handling of Home Credit competition access, use, redistribution, publication, derived metadata, and source-text reproduction.

It records narrow project decisions based on authoritative terms inspected on 2026-09-06. It is not legal advice, a legal-rights declaration, a compliance certification, or permission for any use beyond the exact handling described here.

The technical behavior required of a future acquisition implementation lives in [the acquisition contract](home-credit-acquisition-contract.md). Source provenance and semantics remain in the completed Step 1 evidence documents. This assessment does not change them.

## Current Step 3 readiness status

**Blocked — incompatible conditions**

The competition-specific rule limits access and use of Competition Data to competition purposes and expressly supersedes the general rule that otherwise mentions academic, educational, and other non-commercial uses. The planned project use is a public educational portfolio project rather than participation in the closed 2018 competition.

The repository therefore will not acquire or analyze the competition files under the current project purpose. User acceptance of the rules would not, by itself, remove this incompatibility.

Step 3 may begin only after a separately approved source strategy resolves this blocker and the user explicitly authorizes acquisition in a later turn.

## Assessment boundaries

This step separates six permission dimensions:

- **Access:** whether and under what preconditions the files can be obtained.
- **Use:** the purposes for which obtained files may be used.
- **Redistribution:** whether source files or source content may be provided to someone else.
- **Publication:** whether an artifact may be placed in a public repository or portfolio.
- **Derived-metadata publication:** whether calculated facts such as checksums, counts, schemas, or profiles may be published.
- **Source-text reproduction:** whether organizer-authored descriptions may be copied or quoted.

A conclusion in one dimension does not supply a conclusion in another. A working download control does not establish permission to publish its output.

## Intended project uses

### Obtain competition files after personal rules acceptance

- Evidence status: **Explicitly supported by authoritative terms**
- Intended scope supported by the source: access after acceptance for competition purposes.
- Qualification: the user has not confirmed acceptance, and this project is not being conducted to participate in the closed competition.
- Evidence: HC-TERM-001, HC-TERM-002.

### Use competition files for this local educational portfolio project

- Evidence status: **Apparently inconsistent or restricted**
- Reason: direct authoritative restriction.
- Interpretation: the competition-specific rule says Competition Data may be used only for competition purposes and supersedes the broader general-rule language.
- Evidence: HC-TERM-001.

### Publish raw competition files or archives in the public repository

- Evidence status: **Apparently inconsistent or restricted**
- Reason: direct authoritative restriction and conservative project policy.
- Interpretation: the rules restrict publishing, duplicating, transmitting, redistributing, or otherwise making Competition Data available to non-participants.
- Evidence: HC-TERM-001, HC-TERM-002.

### Publish source-derived metadata in the public repository

- Evidence status: **Unresolved**
- Reason: unresolved evidence.
- Interpretation: the reviewed sources do not expressly classify checksums, detailed schemas, profiles, or relational findings. The project will keep them local-only rather than infer permission.
- Evidence: HC-TERM-001, HC-TERM-003.

### Publish original, source-agnostic project code

- Evidence status: **Not expressly addressed**
- Interpretation: the reviewed competition provisions do not grant or deny a general right to publish independently written source-agnostic tooling after the competition. Project policy permits such code only when it contains no Competition Data, derived source content, credentials, private responses, or access-control bypass.
- Evidence: HC-TERM-001, HC-TERM-003.

### Publish independently generated synthetic fixtures

- Evidence status: **Not expressly addressed**
- Interpretation: project policy permits independently generated synthetic material that contains no copied rows, source values, restricted metadata, or substantial source text and is visibly labeled synthetic.
- Evidence: repository provenance constraints; HC-TERM-001 does not address independently generated fixtures.

### Publish concise original documentation with source citations

- Evidence status: **Not expressly addressed**
- Interpretation: project policy permits original analysis and minimal factual source identification. It prohibits substantial copied source text and requires claim-specific attribution.
- Evidence: HC-TERM-003 and repository documentation policy.

## Authoritative term and access sources

### HC-TERM-001 — Home Credit Default Risk competition rules

- Title: Home Credit Default Risk — Competition Rules
- Publisher: Home Credit International a.s., hosted by Kaggle
- Canonical URL: https://www.kaggle.com/competitions/home-credit-default-risk/rules
- Access date: 2026-09-06
- Version or effective date: no revision or effective date displayed; the page displays the competition period ending 2018-08-29
- Access status: inspected publicly without authentication
- Relevant condition: entry constitutes acceptance; the competition-specific data provision says access and use are only for competition purposes and supersedes General Rules Section 7.A
- Additional relevant condition: General Rules Section 7.B restricts transmitting, duplicating, publishing, redistributing, or making Competition Data available to a non-participant and disclaims participant ownership or an implied data license
- Project interpretation: the source directly conflicts with acquiring the files for this public educational portfolio purpose
- Qualification: this is a project-handling conclusion, not a legal opinion about hypothetical uses or enforceability
- Unresolved question: the page does not display a revision history showing whether its text changed after 2018

### HC-TERM-002 — Home Credit Default Risk data page and access gate

- Title: Home Credit Default Risk — Data
- Publisher: Kaggle for the Home Credit competition
- Canonical URL: https://www.kaggle.com/competitions/home-credit-default-risk/data
- Column-description view: https://www.kaggle.com/competitions/home-credit-default-risk/data?select=HomeCredit_columns_description.csv
- Access date: 2026-09-06
- Version or effective date: none displayed
- Access status: public metadata inspected without authentication; file content remained gated
- Relevant condition: the displayed license designation is “Subject to Competition Rules”
- Relevant access gate: viewing or downloading the files requires sign-in or registration and agreement to the competition rules
- Project interpretation: no standalone open-data license was displayed; the competition rules control the data handling assessed here
- Qualification: no sign-in, acceptance, file preview, or download was performed
- Unresolved question: no authenticated account-specific prompt or additional designation was inspected

### HC-TERM-003 — Current Kaggle Terms of Use

- Title: Kaggle Terms of Use
- Publisher: Kaggle Inc.
- Canonical URL: https://www.kaggle.com/terms
- Access date: 2026-09-06
- Version or effective date: June 22, 2025, displayed as active
- Access status: inspected publicly without authentication
- Relevant condition: Kaggle use and access are subject to the terms; competitions also have separate competition rules that may impose additional restrictions
- Relevant content condition: users must respect restrictions attached to content and may not copy or store a significant portion or exploit content without the required consent
- Project interpretation: the current general terms do not expand the narrower competition-specific data-use rule
- Qualification: the current terms are not evidence of the exact terms version a user may have accepted in 2018
- Unresolved question: which historical Kaggle terms version was incorporated at competition launch is not displayed on the competition rules page

### HC-TERM-004 — Kaggle public API documentation

- Title: How to Use Kaggle — Public API
- Publisher: Kaggle
- Canonical URL: https://www.kaggle.com/docs/api
- Access date: 2026-09-06
- Version or effective date: none displayed
- Access status: inspected publicly without authentication
- Relevant condition: programmatic access supports Kaggle CLI or KaggleHub and requires an account-backed authentication method for protected actions
- Project interpretation: authentication mechanics do not accept competition rules and do not establish data-use or publication permission
- Qualification: Step 3 must use the approved CLI path and record the installed tool version at execution time
- Unresolved question: the public page does not state which authentication method will be active for this account at a future acquisition time

### HC-TERM-005 — Official Kaggle CLI competition documentation

- Title: Kaggle CLI — Competitions Commands
- Publisher: Kaggle, in the official `Kaggle/kaggle-cli` repository
- Canonical URL: https://github.com/Kaggle/kaggle-cli/blob/main/docs/competitions.md
- Access date: 2026-09-06
- Version or effective date: mutable `main` branch documentation; no document version displayed
- Access status: inspected publicly without authentication
- Relevant condition: `kaggle competitions download <COMPETITION>` downloads competition files and supports explicit destination paths; its force option can overwrite files
- Project interpretation: Step 3 must provide an explicit ignored path and must not use overwrite behavior
- Qualification: command documentation describes mechanics, not permission; Step 3 must record its installed CLI version and verify live help
- Unresolved question: the exact future installed CLI version and its live behavior are not known during this documentation-only step

### HC-TERM-006 — Official Kaggle CLI authentication documentation

- Title: Kaggle CLI — Authentication
- Publisher: Kaggle, in the official `Kaggle/kaggle-cli` repository
- Canonical URL: https://github.com/Kaggle/kaggle-cli/blob/main/skills/references/auth.md
- Access date: 2026-09-06
- Version or effective date: mutable `main` branch documentation; no document version displayed
- Access status: inspected publicly without authentication
- Relevant condition: the CLI supports user-controlled OAuth, access-token, and legacy credential sources
- Project interpretation: the user must choose and configure authentication outside the repository; project tooling may test authentication without reading or printing credential values
- Qualification: no credential source was inspected and no authentication command was run
- Unresolved question: the user has not selected or configured an authentication method for this project

## Source precedence and interpretation

The competition-specific rule expressly replaces the general competition data-use clause. This is why the general clause mentioning academic, educational, and non-commercial purposes does not support the planned portfolio use.

The current Kaggle terms remain relevant to use of the platform, content handling, and source reproduction, but they do not erase a more specific competition condition.

The winner-license provision concerns a winner's submission and source code. It does not grant a participant permission to republish Competition Data and is not used for any data-publication conclusion.

## Permission-dimension findings

### Access

- Finding: file access is conditioned on personal sign-in or registration and agreement to the competition rules.
- Evidence classification: direct authoritative condition.
- Evidence: HC-TERM-001, HC-TERM-002.
- Project handling: no access attempt until the purpose conflict is resolved, the user personally completes required actions, and the user later authorizes Step 3.

### Use

- Finding: the competition-specific rule restricts Competition Data use to competition purposes.
- Evidence classification: direct authoritative restriction.
- Evidence: HC-TERM-001.
- Project handling: acquiring or analyzing the data for this portfolio purpose is blocked.

### Redistribution

- Finding: the rules restrict providing Competition Data to non-participants.
- Evidence classification: direct authoritative restriction.
- Evidence: HC-TERM-001.
- Project handling: original files, archives, and real rows are prohibited from Git or other public delivery.

### Publication

- Finding: the rules expressly include publishing within the restricted ways of making Competition Data available.
- Evidence classification: direct authoritative restriction.
- Evidence: HC-TERM-001.
- Project handling: Competition Data is prohibited from the public repository.

### Derived-metadata publication

- Finding: the reviewed sources do not expressly classify derived facts such as checksums, full schemas, profiles, or relationship statistics.
- Evidence classification: unresolved evidence.
- Evidence: HC-TERM-001, HC-TERM-003.
- Project handling: source-derived metadata remains local-only pending resolution; silence is not permission.

### Source-text reproduction

- Finding: current Kaggle terms require respect for content restrictions and restrict copying or storing a significant portion of platform content.
- Evidence classification: direct authoritative condition plus conservative project policy.
- Evidence: HC-TERM-003.
- Project handling: substantial copied source text is prohibited. Original concise paraphrase with claim-specific citations is preferred. Any later exact quotation requires individual review.

## Artifact handling classifications

Each category below has one current project-handling classification.

### Raw CSV files

- Classification: **Prohibited — direct authoritative restriction**
- Reason: Competition Data may not be published or redistributed to non-participants; portfolio use is also outside the stated competition-only purpose.
- Evidence: HC-TERM-001, HC-TERM-002.

### Original downloaded archive

- Classification: **Prohibited — direct authoritative restriction**
- Reason: the archive is Competition Data and must not enter Git or public delivery.
- Evidence: HC-TERM-001, HC-TERM-002.

### Real row samples

- Classification: **Prohibited — direct authoritative restriction**
- Reason: publishing even selected rows would make Competition Data available outside the controlled participant context.
- Evidence: HC-TERM-001.

### `HomeCredit_columns_description.csv`

- Classification: **Prohibited — direct authoritative restriction**
- Reason: the official data page lists it inside the competition bundle governed by the competition rules.
- Evidence: HC-TERM-001, HC-TERM-002.
- Qualification: its content remains deferred and uninspected.

### File names

- Classification: **Permitted by project policy**
- Reason: the names are publicly displayed source identifiers needed for narrow provenance and acquisition-contract references; reviewed terms do not identify a restriction preventing that specific minimal handling.
- Evidence: HC-TERM-002.
- Qualification: this does not permit copying accompanying descriptions or file contents.

### SHA-256 checksums

- Classification: **Local-only pending resolution**
- Reason: unresolved evidence.
- Evidence: HC-TERM-001, HC-TERM-003.

### File sizes

- Classification: **Local-only pending resolution**
- Reason: unresolved evidence for source-derived per-file metadata.
- Evidence: HC-TERM-001, HC-TERM-003.

### Row and column counts

- Classification: **Local-only pending resolution**
- Reason: unresolved evidence.
- Evidence: HC-TERM-001, HC-TERM-003.

### Column names

- Classification: **Local-only pending resolution**
- Reason: unresolved evidence; a complete list could reproduce a substantial source structure.
- Evidence: HC-TERM-001, HC-TERM-003.

### Schemas

- Classification: **Local-only pending resolution**
- Reason: unresolved evidence for detailed source-derived structure.
- Evidence: HC-TERM-001, HC-TERM-003.

### Aggregate profiles

- Classification: **Local-only pending resolution**
- Reason: unresolved evidence; aggregates may expose source distributions or rare values.
- Evidence: HC-TERM-001, HC-TERM-003.

### Relational findings

- Classification: **Local-only pending resolution**
- Reason: unresolved evidence for findings computed from the files.
- Evidence: HC-TERM-001, HC-TERM-003.

### Leakage registers

- Classification: **Local-only pending resolution**
- Reason: unresolved evidence; a detailed register may reproduce column names and source-derived interpretations.
- Evidence: HC-TERM-001, HC-TERM-003.

### Synthetic fixtures

- Classification: **Permitted by project policy**
- Reason: conservative project policy permits independently generated, visibly labeled synthetic content that contains no copied rows, source values, restricted metadata, or substantial source text.
- Evidence: repository provenance constraint.
- Qualification: a fixture using source-derived structure must be reassessed rather than presumed synthetic.

### Acquisition code

- Classification: **Permitted by project policy**
- Reason: reviewed terms do not identify a restriction preventing publication of independently written, source-agnostic contract implementation after the competition.
- Evidence: HC-TERM-001, HC-TERM-003, HC-TERM-005.
- Qualification: code must not contain Competition Data, source-derived content, credentials, authenticated responses, or bypass behavior. This classification does not make acquisition ready.

### Manifests

- Classification: **Local-only pending resolution**
- Reason: populated manifests contain source-derived checksums, sizes, and inventory information whose publication treatment is unresolved.
- Evidence: HC-TERM-001, HC-TERM-003.
- Qualification: an empty manifest schema written by the project is original documentation and may be separately handled as project code.

### Source quotations and descriptions

- Classification: **Prohibited — conservative project policy**
- Reason: the project does not need copied source prose and will avoid substantial reproduction.
- Evidence: HC-TERM-003 and repository documentation policy.
- Qualification: concise original paraphrases with claim-specific links are permitted by project policy; any exact short quotation requires individual review.

## User-controlled actions

Only the user may:

- sign in to Kaggle;
- review terms displayed to their account;
- accept or acknowledge competition rules;
- complete account or identity verification;
- create, rotate, or configure Kaggle credentials;
- confirm any intended purpose presented during access;
- explicitly authorize a later Step 3 acquisition.

Codex performed none of these actions. The presence of a credential would not prove rules acceptance, purpose compatibility, or user authorization.

## `HomeCredit_columns_description.csv` treatment

- Access: gated behind sign-in or registration and rules agreement.
- Local retention: not approved for this portfolio purpose under the current competition-only use condition.
- Publication and redistribution: the original file is prohibited by direct authoritative restriction.
- Substantial reproduction: prohibited.
- Short interpretation: only original, claim-specific paraphrase may be published when based on legitimately inspected authoritative material.
- Current evidence state: deferred and uninspected.
- Mirror policy: no unofficial mirror may be used.

## Unresolved issues

- The rules page does not expose revision history or an effective date for its present text.
- The exact historical Kaggle terms incorporated when the competition opened were not established.
- No authenticated, account-specific access prompt was inspected.
- The sources do not expressly classify source-derived checksums, detailed schemas, profiles, or relational findings.
- The sources do not expressly address a post-competition public portfolio scenario separately from the competition-only use restriction.
- No sponsor permission for the planned portfolio use was located.

None of these uncertainties weakens the current blocker. The explicit competition-only purpose is already incompatible with the planned acquisition purpose.

## Stop conditions and next decision

Step 3 must not begin while the readiness status is blocked. A future proposal must address one of these paths before acquisition:

- obtain documented permission from an appropriate authoritative source for the intended use;
- select an alternative source whose terms support the project purpose;
- revise the project to use independently generated synthetic data without representing it as Home Credit source data;
- approve another evidence-backed source strategy.

Any option that changes the current source architecture requires the normal explain-and-approve process before architecture or plans are edited.

## Review triggers

Reassess this document if:

- authoritative terms or the data-page designation change;
- the sponsor or Kaggle provides written clarification;
- the project purpose changes;
- an alternative dataset is proposed;
- a later artifact needs a publication classification not covered here.
