# Authority Model

The authority model separates accountable human authority from delegated agent execution.
It defines who can approve, who can operate, and when work must defer or block.

## Core roles

### Accountable authority

The accountable authority is the final human decision owner for governance boundaries, approval, and escalation acceptance.

### Owner/operator

The owner/operator defines mission intent, approves scope, and decides whether high-impact actions proceed.

### Maintainer/operator

Maintainer/operators implement approved changes within delegated scope and provide evidence and validation outcomes.

### Governed agent

The governed agent executes approved tasks, proposes escalations when needed, and must not self-grant authority.

### Hermes-compatible runtime

The runtime is an execution environment that can host tools, automation, and policy workflows.
Runtime capability does not override governance authority requirements.

## Operational trust versus authority proof

Operational trust describes confidence in execution quality.
Authority proof describes permission to perform an action.
Trust can support approval decisions but cannot replace explicit authority proof.

## No self-granting principle

The agent may classify, propose, and prepare evidence.
The agent must not approve its own authority expansion.

## Delegation boundaries

Delegation boundaries must be explicit across:

- functional scope,
- environment scope,
- time window,
- rollback obligation,
- telemetry expectation.

Outside that boundary, actions defer or block.

## Approval, defer, and block logic

| Condition | Decision |
|---|---|
| Scope is approved, evidence complete, classification valid | Allow |
| Scope is plausible but authority or evidence is incomplete | Defer |
| Scope conflicts with policy or confidentiality/safety constraints | Block |

## Emergency stop logic

Emergency stop should be triggered when:

- active action exceeds approved scope,
- safety controls fail,
- rollback readiness is lost,
- authority conflict is discovered.

Stop action should preserve evidence and notify accountable authority.

## Public-safe role table

| Role | Can classify | Can execute | Can approve escalation | Can alter recovery custody |
|---|---|---|---|---|
| Accountable authority | Yes | Optional | Yes | Yes, with strict controls |
| Owner/operator | Yes | Optional | Yes, within governance model | Usually via accountable authority path |
| Maintainer/operator | Yes | Yes, within approved scope | No | No |
| Governed agent | Yes | Yes, within approved scope | No | No |

## Evidence expectations by role

- authority source reference,
- scope statement,
- pre-change checkpoint evidence,
- post-change validation evidence,
- defer/block rationale when applicable.

## Related concepts

- [Agent Delegated Administration Level (ADAL)](adal.md)
- [Container/Sandbox Delegation Level (CDEL)](cdel.md)
- [External Service Authority Level (ESAL)](esal.md)
- [Project Confidentiality Level (PCL)](pcl.md)
- [Policy gates](policy-gates.md)

Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr
Assisted-by: ChatGPT: GPT-5.5 Thinking; Codex; Hermes Agent v0.13
