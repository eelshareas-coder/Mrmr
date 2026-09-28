# Research Evidence Collector v1

## Purpose

Convert a discovered topic into a traceable verification package without silently upgrading discovery material into verified evidence.

Pipeline:

TOPIC_CANDIDATE → COLLECT → SCREEN → CROSS_CHECK → CLAIM_LEDGER → UNCERTAINTY_REVIEW → VERIFICATION_PACKAGE → VERIFIED_GATE

## Required package

Every verification package must contain:

1. Evidence Card
2. Claim Ledger
3. Source Ledger
4. Uncertainty Notes
5. Audience Framing
6. Red-Flag Review
7. Verification Decision

The package is identified by a stable `verification_package_id` and linked to exactly one `topic_id`.

## Evidence Card

Required fields:

- `topic_id`
- `verification_package_id`
- `question`
- `scope`
- `audience`
- `summary`
- `evidence_strength`
- `evidence_as_of`
- `sensitivity_level`

Evidence strength is descriptive, not a numerical score:

- `strong`
- `moderate`
- `limited`
- `mixed`
- `insufficient`

Do not use strength labels to imply certainty beyond the underlying sources.

## Claim Ledger

Every factual statement intended for production must be a separate claim record.

Required claim fields:

- `claim_id`
- `claim_text`
- `claim_type`: FACT | INTERPRETATION | UNCERTAINTY | OPINION
- `source_ids`
- `support_status`: SUPPORTED | PARTIAL | CONTESTED | UNSUPPORTED
- `scope_or_population`
- `time_boundary`
- `wording_limit`

A claim cannot be `SUPPORTED` without at least one source record. Sensitive claims require the minimum tier defined by SOURCE-REGISTRY-v1.yml.

## Source Ledger

Each source record must contain:

- `source_id`
- `title`
- `publisher`
- `url`
- `tier`
- `publication_date` when available
- `accessed_at`
- `status`
- `supports_claim_ids`
- `notes`

Source status:

- `screened`
- `verified`
- `rejected`
- `stale`

A URL alone is not evidence verification. The collector must record what the source actually supports.

## Cross-check rules

- Important factual claims should be checked against more than one independent source when practical.
- A single source must not be generalized beyond its population, design, setting, date, or stated outcome.
- Correlation must not be rewritten as causation.
- Study results must retain relevant limitations.
- Conflicting evidence is recorded, not hidden.
- Secondary sources may help discover or contextualize a claim but do not replace required primary/authoritative evidence for sensitive claims.

## Uncertainty Notes

Record:

- unresolved disagreement;
- missing population/context;
- evidence that is preliminary or limited;
- outdated or superseded guidance;
- claims that require narrower wording;
- information the production team must not imply.

If uncertainty changes the meaning of a claim, the claim remains `PARTIAL`, `CONTESTED`, or `UNSUPPORTED` until resolved.

## Verification decision

Allowed decisions:

- `VERIFIED`
- `HOLD`
- `RESEARCH_MORE`
- `REJECTED`

A package may be marked `VERIFIED` only when:

- all required package sections exist;
- every production claim has a source mapping;
- no production claim is `UNSUPPORTED`;
- required source tiers are satisfied;
- uncertainty notes are present, including an explicit empty list when none remain;
- red-flag review is complete;
- the package passes the machine-checkable schema;
- the episode brief references the same verification package.

Otherwise the topic cannot enter the VERIFIED state.

## Failure isolation

Collector failures must:

1. preserve the last valid package;
2. record the failure;
3. leave QA, safety, rights, access controls, audit logging, and publishing gates enabled;
4. block VERIFIED transition until the package is repaired and revalidated.

The collector never edits scientific claims merely to make validation pass.

## Handoff

On VERIFIED:

`verification_package_id` → Episode Brief → EXECUTIVE_REVIEW.

The evidence package is immutable for that episode version. A material evidence change creates a new package version and reopens verification.
