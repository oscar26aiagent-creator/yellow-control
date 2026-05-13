# GitHub Governance

Status: v0.1.3 clean architecture rebuild candidate.
Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr

## Purpose

Define governance workflow for repository operations as an external-access workflow.

## Scope

This procedure covers branch-based contribution and review flows.
It does not grant ownership-level account authority.

## Baseline rules

- Classify action under ESAL and PCL before execution.
- Prefer fork and pull request workflow.
- Keep changes scoped and reviewable.
- No direct upstream push without explicit authority.

## Standard workflow

1. Confirm repository target and approved remote.
2. Create or switch to scoped working branch.
3. Apply changes and run required validations.
4. Commit with clear message.
5. Push to approved remote scope.
6. Open review request when required.
7. Record governance decision summary.

## High-risk actions

The following require elevated approval:

- force push on shared protected branch;
- branch protection changes;
- ownership or recovery changes;
- destructive history rewrites on canonical branch.

## Decision handling

| Condition | Decision |
|---|---|
| Fork-scope branch update with validated docs | Allow |
| Ambiguous remote ownership or branch target | Defer |
| Unauthorized upstream write request | Block |

## Related documents

- [External Access Register](../registers/external-access-register.md)
- [Policy Gates](../concepts/policy-gates.md)
