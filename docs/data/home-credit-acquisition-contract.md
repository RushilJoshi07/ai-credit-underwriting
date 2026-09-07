# Home Credit Acquisition Contract

## Purpose and authority

This document is the authoritative technical contract for any future implementation that acquires the Home Credit competition bundle. It specifies deterministic safety and provenance behavior but does not perform or authorize acquisition.

[The access, use, and publication assessment](home-credit-access-and-licensing.md) controls whether Step 3 is ready. If that assessment blocks acquisition, this contract remains a design artifact only.

This content-identity scheme is project-defined. It is not presented as an external industry standard.

## Current implementation state

- No acquisition code exists.
- No dataset or archive has been downloaded.
- No authentication has been attempted.
- No competition terms have been accepted by Codex.
- The user has not authorized Step 3.

## Fixed source identifiers

- Competition slug: `home-credit-default-risk`
- Competition page: https://www.kaggle.com/competitions/home-credit-default-risk
- Data page: https://www.kaggle.com/competitions/home-credit-default-risk/data
- Rules page: https://www.kaggle.com/competitions/home-credit-default-risk/rules
- Acquisition channel: official Kaggle CLI against Kaggle's official service
- Mirror policy: third-party mirrors are prohibited

## Preconditions for Step 3

All of these must be true before any network acquisition:

- The access assessment no longer reports a blocking readiness status.
- The user has personally reviewed and completed every binding account action required by Kaggle.
- The user explicitly authorizes Step 3 in a later turn.
- The approved local destination is protected by `.gitignore`.
- The installed acquisition tool and version have been recorded.
- Available disk space satisfies the pre-download check.
- No destination selected for the event or snapshot already contains conflicting content.

Failure of any precondition must stop before download.

## User-controlled authentication boundary

The user controls sign-in, rules acceptance, account verification, and credential creation or configuration.

Step 3 tooling may ask the Kaggle CLI to use an already configured authentication source. It must not:

- open or complete an interactive acceptance flow on the user's behalf;
- read credential values into project metadata;
- print tokens, cookies, usernames, keys, or authenticated response bodies;
- copy machine-level credentials into the repository;
- infer rules acceptance from authentication success;
- manage global machine credential or cache paths through project `.gitignore`.

Authentication failure stops the acquisition without fallback to scraping, browser-cookie export, or a mirror.

## Repository-local storage layout

All downloaded and extracted source bytes remain under ignored `data/raw/` paths:

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

`event.json`, `identity.json`, archives, work files, and extracted files are local-only under the current publication assessment.

The tracked `data/raw/README.md` is the only approved tracked file in the raw directory.

## Acquisition ID

An Acquisition ID identifies one particular acquisition attempt, including failed or repeated attempts.

Format:

```text
acq-<lowercase UUIDv4 hex>
```

Requirements:

- Generate a random UUID version 4.
- Remove hyphens and encode its 32 hexadecimal characters in lowercase.
- Prefix the value with `acq-`.
- Create a new Acquisition ID before each network download attempt.
- Never reuse an Acquisition ID.
- Do not derive it from content, time, machine path, or account identity.

Acquisition-event metadata records:

- Acquisition ID;
- event start and completion times in UTC;
- competition slug and official source URLs;
- acquisition tool name and exact version;
- requested destination represented by repository-relative logical path;
- archive filename, byte size, and complete SHA-256 when available;
- event result: `started`, `failed`, or `complete`;
- failure category without credential or private-response content;
- resulting snapshot/content ID when validation completes.

Acquisition timestamps describe the event. They do not affect snapshot/content identity.

## Snapshot/content ID

A Snapshot/content ID identifies the logical extracted source content deterministically.

It excludes:

- acquisition time;
- Acquisition ID;
- machine-specific or absolute paths;
- account identity;
- credential source;
- CLI version;
- archive container metadata.

### Eligible inventory entries

Only extracted regular files may enter the normalized identity inventory.

Reject:

- directories as inventory entries;
- symbolic links;
- hard links;
- devices, sockets, named pipes, or other special files;
- absolute paths;
- paths containing a backslash;
- empty paths;
- `.` or `..` path segments;
- path segments containing Unicode control characters;
- two paths that become identical after normalization.

### Path normalization

For every regular file:

1. Decode the archive path using the archive format's declared or safely supported encoding. Fail rather than guess after a decoding error.
2. Require a relative POSIX-style path using `/` separators.
3. Normalize each path segment to Unicode Normalization Form C (NFC).
4. Reject empty, `.`, or `..` segments after normalization.
5. Reject characters in the Unicode `Cc` control category.
6. Rejoin segments with `/`.
7. Reject duplicate normalized paths.

The normalized path is relative to the snapshot `files/` root and never contains that local root itself.

### Per-file evidence

For each normalized regular file, compute:

- `path`: normalized relative POSIX path;
- `size_bytes`: exact non-negative integer byte length;
- `sha256`: complete lowercase 64-character SHA-256 of the file bytes.

Sort file records by the UTF-8 byte sequence of `path`, ascending. No locale-aware or case-folded ordering is allowed.

### Canonical identity object

Construct exactly this logical JSON object:

```json
{
  "competition_slug": "home-credit-default-risk",
  "files": [
    {
      "path": "<normalized-relative-path>",
      "sha256": "<complete-lowercase-sha256>",
      "size_bytes": 0
    }
  ],
  "identity_schema": "hcdr-content-identity-v1"
}
```

The `files` array contains all eligible records in the required order. `size_bytes` above illustrates the integer field; it is replaced by each file's actual byte size.

### Canonical JSON serialization

Serialize the identity object with these project-defined rules:

- UTF-8 encoding;
- Unicode emitted directly rather than ASCII escape substitution;
- object keys sorted lexicographically by Unicode code point;
- array order preserved;
- `,` between array or object items with no following space;
- `:` between keys and values with no following space;
- standard JSON string escaping;
- no byte-order mark;
- no leading or trailing whitespace;
- no trailing newline.

The identity object contains only strings, non-negative integers, arrays, and objects. Floating-point values, nulls, and booleans are not allowed.

### Content digest and ID

Compute the complete SHA-256 of the canonical JSON bytes.

The snapshot/content ID is:

```text
hcdr-v1-<full-content-digest>
```

`<full-content-digest>` is the complete lowercase 64-character SHA-256. Truncated hashes are not authoritative identifiers.

## Archive identity and content identity

Archive byte identity is recorded separately using:

- original archive filename;
- exact archive size in bytes;
- complete lowercase SHA-256 of the archive bytes.

The archive SHA-256 is not an input to snapshot/content identity. Therefore:

- repeated byte-identical content can create a new Acquisition ID and resolve to the same snapshot/content ID;
- changed extracted paths, sizes, or bytes produce a different snapshot/content ID;
- differently packaged archives can have different archive hashes but the same logical snapshot/content ID when their normalized extracted files are identical.

Both archive and file hashes remain required integrity evidence.

## Write-once and no-overwrite behavior

- Acquisition tooling never changes an archive or extracted raw file in place.
- An Acquisition ID directory is created only when absent.
- A snapshot is first assembled under the event's ignored `work/` path.
- Existing snapshot directories are never extraction destinations.
- After content identity is computed, a new snapshot directory may be promoted only if its final ID path does not exist.
- If the final snapshot path exists, recompute and compare its canonical identity and every file hash.
- Matching content is referenced by the new event without overwriting the existing snapshot.
- Any disagreement fails closed as an integrity conflict.
- Reacquisition never updates an old snapshot to look like new content.
- Transformations and analytical outputs must be written outside raw storage.

This is logical immutability enforced by project tooling. It is not filesystem-level immutability.

## Disk-space checks

Step 3 must perform two checks:

1. Before download, compare available space with the best authoritative published bundle size plus space reserved for the archive, extraction, and temporary work. If the source does not provide enough sizing information to establish a safe reserve, stop and require an explicit operator-provided minimum.
2. After download but before extraction, inspect archive metadata without extracting. Sum declared uncompressed regular-file sizes using overflow-safe integer arithmetic and require enough free space for extraction plus temporary promotion overhead.

Archive metadata is untrusted. Implausible sizes, compression ratios, duplicate entries, integer overflow, or insufficient space must stop extraction.

## Download behavior

- Use the official Kaggle CLI with competition slug `home-credit-default-risk`.
- Record the exact live CLI version and relevant help output before execution.
- Supply the new event's ignored archive directory explicitly.
- Do not use the CLI force/overwrite option.
- Refuse a non-empty archive destination.
- Preserve the exact downloaded archive bytes.
- Compute archive size and SHA-256 before extraction.
- Never fall back to a mirror or browser scraping.

## Secure extraction

Before writing any extracted file:

- enumerate and validate the complete archive entry list;
- reject absolute, drive-qualified, or network paths;
- reject empty, dot, dot-dot, backslash, control-character, and normalized-duplicate paths;
- resolve the proposed destination and verify it remains under the staging root;
- reject symbolic links, hard links, devices, sockets, pipes, and unsupported special types;
- reject duplicate archive entries and case-insensitive collisions that would be unsafe on the active filesystem;
- refuse any existing destination path;
- enforce declared and configured size limits;
- extract only into the new event staging directory.

After extraction, independently walk the staging directory without following links. Reject unexpected files before computing the normalized inventory.

## Manifest requirements

The local event manifest must include:

- manifest schema version;
- Acquisition ID;
- UTC event timestamps;
- competition slug and canonical source URLs;
- acquisition tool and exact version;
- event status and sanitized failure category;
- archive relative logical path, filename, size, and full SHA-256;
- resulting snapshot/content ID;
- verification timestamp and result.

The local snapshot identity manifest must include:

- identity schema version;
- competition slug;
- snapshot/content ID;
- canonical inventory entries;
- full per-file SHA-256 values and sizes;
- canonical identity JSON SHA-256;
- verification timestamp and result.

No manifest may contain:

- an absolute machine path;
- username, email, account ID, or credential source details;
- tokens, keys, cookies, authorization headers, or private response content;
- unredacted stack traces containing sensitive environment data.

Populated manifests remain local-only under the current publication assessment.

## Trust states and failure behavior

Allowed snapshot trust states are:

- `unverified`;
- `verified`;
- `untrusted`.

A snapshot becomes `verified` only after archive validation, safe extraction, inventory construction, content-ID computation, file-hash recomputation, and manifest reconciliation all succeed.

Any checksum mismatch, identity disagreement, unexpected inventory entry, overwrite condition, unsafe path, unsupported file type, or incomplete manifest makes the event fail and leaves affected content `untrusted`.

An untrusted snapshot cannot be read by later inventory, validation, or modeling steps.

## Verification before later analysis

Before each later raw analysis:

- load the expected local snapshot identity manifest;
- recompute the normalized file inventory;
- recompute every full file SHA-256;
- recompute the canonical identity digest;
- confirm the snapshot/content ID;
- confirm trust state is `verified`;
- open raw files read-only;
- refuse analysis on any mismatch.

Verification establishes byte identity and contract conformance. It does not establish semantic correctness, permission, representativeness, or model suitability.

## Step 3 implementation acceptance criteria

If a future approved source strategy makes Step 3 ready, its implementation must prove with synthetic tests that:

- Acquisition IDs have the exact UUIDv4 format and are never reused;
- acquisition timestamps do not influence content IDs;
- normalized identical inventories produce identical content IDs;
- any normalized path, size, or byte-hash change produces a different content ID;
- repackaged identical extracted content resolves to the same content ID;
- traversal, links, special files, duplicate paths, and overwrite attempts are rejected;
- complete SHA-256 values are recorded and reverified;
- credentials and absolute paths never enter manifests;
- raw bytes are not tracked by Git;
- a checksum or identity mismatch blocks later analysis.

Local integration against source data remains forbidden until the access assessment changes and the user explicitly authorizes acquisition.
