# Server First Contact

Status: v0.1.3 clean architecture rebuild candidate.
Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr

## Purpose

Define the mandatory first-contact sequence for server-class external targets.
This procedure is safety-first and defaults to defer or block when information is incomplete.

## Preconditions

- Target exists in external access register.
- Required ADAL/CDEL/ESAL/PCL classifications are present.
- Approval scope is explicit.
- Backup and rollback gate is satisfied.

## Procedure

1. Confirm target entry exists in [External Access Register](../registers/external-access-register.md).
2. Confirm first-contact status and required approvals.
3. Create governance checkpoint before contacting the target.
4. Validate authority and allowed action scope.
5. Perform reachability and identity checks only.
6. Run read-only baseline audit only.
7. Do not run arbitrary elevated commands.
8. Do not use container socket or privileged container actions unless explicitly approved.
9. Record concise evidence summary and update register status.
10. If any required item is unknown, defer or block and report missing evidence.

## Explicit prohibitions

- No arbitrary privileged shell execution.
- No implicit escalation beyond approved scope.
- No plaintext secret disclosure in notes or reports.

## Evidence expectations

Record:

- time and target ID;
- checks performed;
- outcome and decision;
- follow-up requirements;
- reference to evidence artifact location.

## Decision handling

| Condition | Decision |
|---|---|
| All prerequisites satisfied, read-only checks only | Allow |
| Missing approval or incomplete target metadata | Defer |
| Unregistered target or prohibited request | Block |

## Related documents

- [External Access Onboarding](external-access-onboarding.md)
- [Backup and Rollback](../concepts/backup-and-rollback.md)
- [Policy Gates](../concepts/policy-gates.md)
