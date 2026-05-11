# Agent Delegated Administration Level (ADAL)

ADAL is the governance scale for delegated administration actions performed by an agent in a runtime or host context.

## Purpose

ADAL defines bounded operational authority so actions can be reviewed consistently before execution.
It gives a shared language for approval, defer, and block decisions.

## Why ADAL exists

Without explicit delegation levels, an agent can appear capable while lacking legitimate authority.
ADAL reduces that ambiguity and forces explicit boundaries before risky actions.

## Relationship with PAM/IAM

PAM and IAM define identities, privilege plumbing, and access controls.
ADAL defines what delegated actions are approved for the agent role.
A valid identity is necessary but not sufficient for high-impact operations.

## No self-granting principle

An agent can propose escalation but cannot grant escalation to itself.
Escalation requires accountable human approval plus evidence.

## ADAL level table

| Level | Delegated scope | Typical allow examples | Typical defer/block examples |
|---|---|---|---|
| ADAL-0 | Read-only interpretation and planning | Read governance docs, classify a request, draft a proposal | Any direct runtime mutation |
| ADAL-1 | Non-privileged local execution | Non-destructive checks, lint, docs updates | Privileged host/service changes |
| ADAL-2 | Controlled operational edits | Approved repository and config edits in bounded scope | Unapproved privileged escalation |
| ADAL-2.5 | Wrapper-mediated privileged task | Run approved narrow wrapper with logs and guardrails | Free-form privileged shell usage |
| ADAL-3 | Broad privileged maintenance | Time-bound approved maintenance activity | Persistent uncontrolled automation |
| ADAL-4 | Recovery-sensitive authority | Controlled break-glass procedures with explicit authority | Recovery ownership mutation without authority |

## ADAL-2.5 wrapper pattern (public-safe)

ADAL-2.5 uses narrow wrappers instead of unrestricted privileged shells.
A compliant wrapper should enforce:

- strict input validation,
- limited command surface,
- deny-by-default unknown options,
- decision and execution telemetry,
- explicit failure signaling.

This preserves operational capability while minimizing privilege spread.

## Escalate, defer, block examples

| Scenario | Decision | Reason |
|---|---|---|
| Classify a change request and produce gate checklist | Allow | ADAL-0 read/analysis scope |
| Execute approved wrapper with checkpoint evidence | Allow | ADAL-2.5 scoped privileged action |
| Request unrestricted root-level shell operation | Defer or block | Scope exceeds delegated controls |
| Modify account recovery ownership settings | Block by default | Recovery custody risk |

## Required evidence before escalation

Before approving escalation, collect:

- purpose and scope statement,
- affected systems and blast radius estimate,
- pre-change backup/checkpoint evidence,
- rollback method and success criteria,
- accountable authority approval record.

Missing evidence should default to defer or block.

## What must remain private

Public-facing docs must not include:

- credentials, tokens, or secret values,
- real recovery custody artifacts,
- private host inventories,
- sensitive runtime logs or identifiers.

## Related concepts and registers

- [Container/Sandbox Delegation Level (CDEL)](cdel.md)
- [Policy gates](policy-gates.md)
- [Backup and rollback](backup-and-rollback.md)
- [Project register](../registers/project-register.md)
- [Runtime register](../registers/runtime-register.md)
- [External service register](../registers/external-service-register.md)

Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr
Assisted-by: ChatGPT: GPT-5.5 Thinking; Codex; Hermes Agent v0.13
