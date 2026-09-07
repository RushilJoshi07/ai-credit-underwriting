# Raw Data Storage

## Current status

No Home Credit archive, CSV, metadata file, or real row has been downloaded or stored here.

Stage 1 Step 3 is blocked under [the current access assessment](../../docs/data/home-credit-access-and-licensing.md). Do not manually place Home Credit files in this directory as a workaround.

## Purpose

This path is reserved for local, ignored, unmodified historical source snapshots if a later approved source strategy permits acquisition.

The tracked README documents the boundary. Everything else under `data/raw/` is ignored by Git unless a future reviewed rule explicitly says otherwise.

## Planned local layout

```text
data/raw/home-credit-default-risk/
  acquisitions/<acquisition-id>/
    event.json
    archive/<official-archive-name>
    work/
  snapshots/<snapshot-content-id>/
    identity.json
    files/<normalized-source-files>
```

This layout is not implemented and does not mean a snapshot exists.

## Safety rules

- Use only an approved official source.
- Never use an unofficial mirror to bypass an access condition.
- Never commit archives, raw files, real rows, populated manifests, or unresolved derived metadata.
- Never place credentials, cookies, tokens, or authenticated responses here.
- Never modify a raw archive or extracted file in place.
- Never overwrite an existing acquisition or snapshot directory.
- Write transformations and analytical outputs outside raw storage.
- Treat any checksum or identity mismatch as loss of trust.
- Open verified raw files read-only during later analysis.

These are project-tooling guarantees, not filesystem-level immutability.

## Identity distinction

- An Acquisition ID identifies one download event and has format `acq-<lowercase UUIDv4 hex>`.
- A snapshot/content ID identifies normalized extracted content and has format `hcdr-v1-<full-content-digest>`.
- Repeated acquisition events may reference the same logical content.

The complete algorithm and secure-extraction requirements are authoritative in [the acquisition contract](../../docs/data/home-credit-acquisition-contract.md).

## User-controlled boundary

Only the user may sign in, review or accept binding terms, configure Kaggle credentials, and explicitly authorize a future acquisition step. Codex must not infer those actions from this directory or from the presence of credentials.
