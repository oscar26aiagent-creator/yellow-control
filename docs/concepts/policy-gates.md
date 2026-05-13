# Policy Gates

Status: v0.1.3 clean architecture rebuild candidate.
Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr

## Purpose

Policy gates convert governance doctrine into repeatable allow, defer, or block decisions.
They are evaluated before execution of privileged, external, or confidentiality-sensitive actions.

## Core gate set for v0.1.3

1. Authority gate
2. Classification and scope gate
3. Backup and rollback gate
4. External access and register gate
5. Confidentiality and publication gate
6. Automation and persistence gate

## 1) Authority gate

Checks whether accountable authority and delegated operator scope are valid.

Allow when:

- authority is explicit and in-scope;
- no self-granting behavior.

Defer when:

- approval is missing or ambiguous;
- delegated scope is unclear.

Block when:

- requested action violates explicit authority boundaries.

## 2) Classification and scope gate

Checks ADAL/CDEL/ESAL/PCL classification and action scope consistency.

Allow when classifications are explicit and consistent.
Defer when one or more classifications are unknown.
Block when requested action conflicts with classified risk bounds.

## 3) Backup and rollback gate

Checks whether risky actions have checkpoint and rollback readiness.

Allow when pre-change checkpoint exists and rollback method is defined.
Defer when evidence is partial.
Block when risky changes are requested without rollback readiness.

## 4) External access and register gate

Checks whether external targets are registered and access-chain evidence is available.

Allow when target registration and approval are complete.
Defer when target metadata is incomplete.
Block when unregistered privileged external action is requested.

## 5) Confidentiality and publication gate

Checks that publication and evidence sharing respect PCL boundaries.

Allow when content is public-safe.
Defer when classification review is needed.
Block when restricted or confidential data would be exposed.

## 6) Automation and persistence gate

Checks creation or modification of persistent automation and long-lived governance effects.

Allow when explicitly approved and auditable.
Defer when persistence impact is unclear.
Block when uncontrolled automation would bypass governance authority.

## Decision table

| Gate | Allow criteria | Defer criteria | Block criteria |
|---|---|---|---|
| Authority | Explicit accountable authority and delegated scope | Missing approval reference | Explicit authority violation |
| Classification and scope | ADAL/CDEL/ESAL/PCL resolved | Any unknown classification | Action exceeds classified bounds |
| Backup and rollback | Checkpoint + rollback readiness confirmed | Evidence incomplete | Risky change without rollback path |
| External access and register | Target entry and access chain validated | Metadata incomplete | Unregistered privileged external action |
| Confidentiality and publication | PCL reviewed and safe for intended audience | Classification uncertain | Restricted data exposure risk |
| Automation and persistence | Explicit approval and auditability | Persistence impact unclear | Uncontrolled long-lived automation |

## Required evidence table

| Evidence item | Why required |
|---|---|
| Classification summary | Proves action risk is understood |
| Scope and target statement | Prevents scope drift |
| Approval reference | Confirms human authority chain |
| Pre-change checkpoint reference | Enables controlled rollback |
| Post-change validation summary | Confirms outcome and safety |

## Fictional examples

Example A: branch documentation push to owned fork with clear scope and no sensitive content.
Likely result: allow.

Example B: external dashboard policy update with missing approval and unknown custody.
Likely result: defer.

Example C: privileged host modification requested with no rollback readiness.
Likely result: block.

## Telemetry expectations

Each decision should produce concise telemetry:

- action summary;
- gate results;
- decision outcome;
- evidence references;
- defer or block rationale.

Telemetry must avoid plaintext secrets and sensitive private artifacts.

## Related documentation

- [Authority Model](authority-model.md)
- [ADAL](adal.md)
- [CDEL](cdel.md)
- [ESAL](esal.md)
- [PCL](pcl.md)
- [Backup and Rollback](backup-and-rollback.md)
