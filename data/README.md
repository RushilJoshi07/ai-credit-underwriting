# Data Area

## Current status

No historical dataset has been acquired. Stage 1 Step 2 found that the Home Credit competition's data-use condition is incompatible with the current public educational portfolio purpose, so Step 3 is blocked.

See [the access, use, and publication assessment](../docs/data/home-credit-access-and-licensing.md) for the evidence and current readiness status.

## Purpose

This directory will keep data categories visibly separate if an approved source strategy later permits implementation. A path does not itself grant access, use, or publication permission.

## Provenance categories

### Historical source data

Original source bytes belong only under ignored `data/raw/` paths and remain governed by source-specific handling rules.

### Engineered model features

Engineered features are not part of Stage 1 and do not yet exist. Later derived data must not overwrite or masquerade as raw source data.

### Synthetic demonstration data

Independently generated synthetic identities and workflow fields remain separate from historical source data. Stage 1 may later use tiny synthetic structural fixtures only after their approved step.

### Fictional internal policy

Policy content is not data-source evidence and does not belong in historical or engineered data paths.

### Authoritative regulatory material

Regulatory sources require their own provenance and must not be mixed with historical applicant data or fictional policy.

## Planned directory roles

- `data/raw/`: ignored historical source archives, snapshots, and local manifests; currently empty except for its README.
- `data/manifests/`: future committed metadata only when its publication classification permits it.
- `data/contracts/`: future machine-readable contracts only when their approved step and publication classification permit them.
- `data/interim/`, `data/processed/`, and `data/external/`: reserved by repository hygiene; no current functionality is implied.

## Git safety

The repository must not track:

- raw source files;
- downloaded archives;
- real source rows;
- credentials or authenticated responses;
- source-derived metadata whose publication handling is unresolved;
- local profiles, logs, or temporary acquisition output.

Tracked READMEs document boundaries; they are not evidence that local data exists.

## Acquisition boundary

Any future acquisition must satisfy both:

- [the access, use, and publication assessment](../docs/data/home-credit-access-and-licensing.md);
- [the technical acquisition contract](../docs/data/home-credit-acquisition-contract.md).

The user must explicitly authorize Step 3 in a later turn even if project readiness changes.
