# Container/Sandbox Delegation Level (CDEL)

CDEL defines delegated authority within container and sandbox execution boundaries.
It separates container-local action from host-impacting risk.

## Purpose

CDEL prevents false assumptions that container access is automatically safe.
It provides a boundary-aware decision model for allow, defer, and block outcomes.

## CDEL level table

| Level | Boundary posture | Typical allow examples | Typical defer/block examples |
|---|---|---|---|
| CDEL-0 | Read-only sandbox visibility | Inspect metadata and approved logs | Any mutation |
| CDEL-1 | Non-privileged container tasks | Run tests, compile, static checks | Host namespace mutation |
| CDEL-2 | Controlled container mutation | Scoped package/config edits in container | Host filesystem writes |
| CDEL-3 | Privileged container operations | Approved maintenance in elevated container | Unapproved host escape vectors |
| CDEL-4 | Host-adjacent orchestration impact | Controlled platform-level config changes with approval | Unbounded cluster-wide authority changes |

## Sandbox, container, and host boundaries

Containers are isolation controls, not absolute trust boundaries.
Boundary weakening patterns include privileged mode, broad host mounts, and over-permissive namespace sharing.
When those patterns exist, CDEL classification should increase accordingly.

## Safe versus risky authority examples

| Pattern | Assessment | Rationale |
|---|---|---|
| Non-privileged docs build in isolated container | Safer | Minimal host interaction |
| Test execution with read-only mounts | Safer | Controlled write surface |
| Container with host root mounted read-write | Risky | Effective boundary collapse |
| Privileged container with unrestricted device access | Risky | Expanded host impact potential |

## Defer and block examples

| Scenario | Decision | Reason |
|---|---|---|
| Run non-privileged test suite in sandbox | Allow | Fits CDEL-1 scope |
| Add privileged runtime flag for convenience | Defer | Needs explicit authority and justification |
| Attempt host namespace manipulation from container | Block by default | Boundary bypass risk |

## Relationship with ADAL

ADAL and CDEL are complementary:

- ADAL governs delegated administration authority,
- CDEL governs sandbox/container boundary authority.

A task can be low ADAL and still high CDEL risk if boundary controls are weak.
Both classifications should be evaluated together.

## Required evidence for higher CDEL actions

Before higher CDEL approval, gather:

- runtime configuration summary,
- mount/network privilege review,
- host-impact statement,
- rollback or recreate strategy,
- accountable approval evidence.

## Operational guardrails

- prefer least-privilege container defaults,
- prefer rebuild-first patterns over manual drift,
- keep elevated permissions temporary,
- record telemetry for each allow/defer/block decision.

## Related concepts and registers

- [Agent Delegated Administration Level (ADAL)](adal.md)
- [Policy gates](policy-gates.md)
- [Backup and rollback](backup-and-rollback.md)
- [Runtime register](../registers/runtime-register.md)

Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr
Assisted-by: ChatGPT: GPT-5.5 Thinking; Codex; Hermes Agent v0.13
