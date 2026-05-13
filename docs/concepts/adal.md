# Agent Delegated Administration Level (ADAL)

Status: v0.1.3 clean architecture rebuild candidate.
Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr

## Purpose

ADAL classifies delegated administrative authority for host and server operations.
It prevents accidental escalation and defines when human approval is mandatory.

## Why ADAL exists

Operational capability alone is not authority.
ADAL separates what is technically possible from what is governance-approved.

## Relationship with PAM and IAM

PAM and IAM provide access control mechanisms.
ADAL adds policy-level delegation boundaries for agent execution.
A valid credential does not automatically imply ADAL permission.

## No self-granting

A governed agent cannot increase ADAL on its own.
Any ADAL expansion requires explicit approval from accountable authority.

## ADAL level table

| Level | Meaning | Typical examples | Default decision |
|---|---|---|---|
| ADAL-0 | No administrative authority | Read public docs, draft proposals | Allow |
| ADAL-1 | Local non-privileged operations | Linting, documentation edits | Allow |
| ADAL-2 | Controlled local maintenance without elevation | Non-privileged service checks | Defer if risk unclear |
| ADAL-2.5 | Root-owned wrapper mediated execution | Approved wrapper for baseline checks | Allow only through wrapper |
| ADAL-3 | Privileged maintenance in bounded scope | Approved package/service changes | Defer unless approved |
| ADAL-4 | High-impact control-plane operations | Security policy or runtime governance changes | Defer by default |
| ADAL-5 | Ownership and recovery authority | Account ownership or irreversible control actions | Block without explicit authority |

## ADAL-2.5 wrapper pattern

ADAL-2.5 allows constrained elevated actions through root-owned audited wrappers.
The wrapper enforces command allowlist, argument validation, logging policy, and exit discipline.
Direct arbitrary elevated shell access is not part of ADAL-2.5.

## Resident runtime versus external target

Resident runtime maintenance may be allowed under a bounded approved workflow.
External target operations require additional external-access checks before execution.
Do not assume host-local approval implies remote-target approval.

## Remote production defaults

For unknown or production-class remote targets:

- default to defer;
- require explicit approval and clear scope;
- require pre-change checkpoint and rollback evidence path.

## Escalation, defer, and block examples

| Scenario | ADAL view | Outcome |
|---|---|---|
| Update local markdown docs | ADAL-1 | Allow |
| Run approved diagnostic wrapper | ADAL-2.5 | Allow with wrapper evidence |
| Direct privileged package modification without approval | ADAL-3+ | Defer |
| Ownership or recovery-setting change requested without authority proof | ADAL-5 | Block |

## Required evidence before escalation

Minimum evidence set:

- action goal and scope;
- target classification and environment;
- gate pre-check results;
- approval reference;
- rollback readiness confirmation.

## What must remain private

Keep out of public docs and commits:

- privileged access artifacts;
- account recovery data;
- sensitive runtime details;
- plaintext secrets.

## Related documentation

- [Authority Model](authority-model.md)
- [Container Delegated Execution Level (CDEL)](cdel.md)
- [External Service Access Level (ESAL)](esal.md)
- [Project Confidentiality Level (PCL)](pcl.md)
- [Policy Gates](policy-gates.md)
- [Backup and Rollback](backup-and-rollback.md)
- [External Access Register](../registers/external-access-register.md)
