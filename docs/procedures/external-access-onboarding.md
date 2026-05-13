# External Access Onboarding

Status: v0.1.3 clean architecture rebuild candidate.
Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr

## Purpose

Describe onboarding for external targets and how onboarding differs by target type.

## Target types

| Type | Typical examples | Key onboarding focus |
|---|---|---|
| server | VM, host, managed node | first-contact safety, baseline evidence |
| api | service endpoints | key reference, scope, rate and write boundaries |
| git | repository hosting | branch/push scope and approval boundaries |
| email | mail providers | send/read scope and account custody |
| cloud | dashboards and control planes | high-impact write boundaries and rollback path |
| identity | identity provider console | recovery custody and ownership controls |

## Common onboarding steps

1. Register target in external access register.
2. Classify ADAL/CDEL/ESAL/PCL requirements.
3. Attach approval model and accountable authority.
4. Add secret references only, never secret values.
5. Define allowed and forbidden action categories.
6. Record first-contact procedure requirement.
7. Validate evidence and mark onboarding status.

## Server-specific note

Server targets must follow [Server First Contact](server-first-contact.md) before broader operations.

## API and service note

For API and service targets, start with read-only verification and explicit write-scope approvals.

## Identity and recovery note

If recovery custody is unknown, onboarding is incomplete and execution must defer.

## Governance outputs

Onboarding should produce:

- updated register entry;
- classification summary;
- approval reference;
- first-contact or first-use evidence summary.

## Related documents

- [External Access Register](../registers/external-access-register.md)
- [Policy Gates](../concepts/policy-gates.md)
- [Secrets Handling](secrets-handling.md)
