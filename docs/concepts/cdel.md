# Container Delegated Execution Level (CDEL)

Status: v0.1.3 clean architecture rebuild candidate.
Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr

## Purpose

CDEL classifies delegated authority for containerized or sandboxed execution.
It describes containment boundaries and escalation risks.

## Why CDEL matters

Container context can be mistaken for safe isolation.
CDEL makes boundary strength explicit and prevents hidden host escalation.

## CDEL level table

| Level | Meaning | Typical examples | Default decision |
|---|---|---|---|
| CDEL-0 | No container interaction | Documentation-only work | Allow |
| CDEL-1 | Read-only container metadata | Inspect image tags and manifests | Allow |
| CDEL-2 | Non-privileged container execution | Run approved read-only checks | Allow with logging |
| CDEL-3 | Elevated container operations | Build/run with expanded permissions | Defer unless approved |
| CDEL-4 | Host-adjacent control | Bind mounts to sensitive paths, host networking changes | Defer by default |
| CDEL-5 | Host-equivalent control through container path | Privileged mode or unsafe socket pathways | Block without explicit authority |

## Boundary model

Container and sandbox boundaries are policy-relevant only when enforced.
A weak boundary can collapse into host-level control.

## High-risk patterns

Examples of high-risk pathways:

- privileged container mode without strict approval;
- unrestricted host mounts;
- docker-socket mediated control chains.

These patterns are treated as high authority even if invoked from a container.

## Safe versus risky examples

| Example | CDEL interpretation | Outcome |
|---|---|---|
| Read-only container image inspection | CDEL-1 | Allow |
| Non-privileged read-only diagnostics in isolated container | CDEL-2 | Allow with controls |
| Launch privileged container for convenience | CDEL-5-like risk | Block unless explicitly approved |
| Use host-sensitive bind mount to modify system state | CDEL-4/5 | Defer or block |

## Relationship with ADAL

ADAL governs host administrative delegation.
CDEL governs containerized execution pathways.
If container action can affect host control, evaluate both ADAL and CDEL and use stricter outcome.

## Defer and block examples

Defer when approval exists in principle but evidence is incomplete.
Block when a prohibited high-risk boundary crossing is requested.

## Required evidence

Before elevated container actions:

- container boundary description;
- expected host impact;
- allowed action list;
- approval reference;
- rollback plan for container-driven host effects.

## Related documentation

- [Authority Model](authority-model.md)
- [Agent Delegated Administration Level (ADAL)](adal.md)
- [External Service Access Level (ESAL)](esal.md)
- [Policy Gates](policy-gates.md)
- [Backup and Rollback](backup-and-rollback.md)
