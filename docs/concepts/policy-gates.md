# Policy Gates

Policy gates are pre-execution controls used to decide whether an action should be allowed, deferred, or blocked.

## Gate model

Each action request is evaluated against multiple gates.
A gate can pass, defer, or fail.
Final decision follows the strictest failing condition.

## Authority gate

Checks that authority source is explicit and valid for requested scope.
If authority proof is missing, decision defaults to defer or block.

## Scope gate

Checks that requested action matches approved task boundaries.
Out-of-scope expansions defer for review.

## Backup gate

Checks that pre-change checkpoint or backup evidence exists where required.
If rollback prerequisite is missing, block runtime-changing actions.

## Rollback gate

Checks that rollback method and success criteria are defined and feasible.
No rollback path means no high-impact change execution.

## Confidentiality gate

Checks PCL classification and publication handling.
Unknown classification defaults to private handling and typically defers publication.

## External-service gate

Checks ESAL scope, ownership/recovery custody clarity, and access-chain validation.
Missing custody metadata or approval evidence should defer or block.

## GitHub/repository gate

Checks branch target, remote safety posture, and contribution policy.
Normal work targets origin fork branch.
Upstream push requires explicit instruction.

## Automation/persistence gate

Checks whether persistent automation changes are explicitly approved.
Unapproved persistence changes defer or block.

## Proposal-only gate

When scope is proposal-only, execution steps are blocked.
Allowed output is documentation, evidence checklist, and recommendation.

## Decision table

| Gate outcome summary | Decision |
|---|---|
| All required gates pass | Allow |
| One or more gates require authority/evidence completion | Defer |
| Safety/confidentiality/authority violation found | Block |

## Required evidence table

| Gate | Minimum evidence |
|---|---|
| Authority gate | Explicit authority source and scope |
| Scope gate | Task boundary statement and impacted areas |
| Backup gate | Checkpoint record or approved backup evidence |
| Rollback gate | Rollback method and validation criteria |
| Confidentiality gate | PCL classification and publication decision |
| External-service gate | ESAL mapping, custody status, approval path |
| Repository gate | Remote/branch verification and push target |
| Automation gate | Explicit approval for persistent automation |

## Fictional examples

| Example action | Gate outcome | Result |
|---|---|---|
| Update public concept docs in feature branch | Authority/scope/repo gates pass | Allow |
| Change org-wide repository protection settings without approval | External-service and authority gates fail | Block |
| Execute maintenance action with incomplete rollback evidence | Rollback gate incomplete | Defer |

## Telemetry expectation

Each decision should emit structured telemetry including:

- action summary,
- applied classifications,
- gate outcomes,
- final decision,
- rationale,
- evidence references.

## Related concepts

- [Authority model](authority-model.md)
- [ADAL](adal.md)
- [CDEL](cdel.md)
- [ESAL](esal.md)
- [PCL](pcl.md)
- [Backup and rollback](backup-and-rollback.md)

Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr
Assisted-by: ChatGPT: GPT-5.5 Thinking; Codex; Hermes Agent v0.13
