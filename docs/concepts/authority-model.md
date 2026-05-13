# Authority Model

Status: v0.1.3 clean architecture rebuild candidate.
Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr

## Purpose

This model defines who is accountable, who executes, and how a governed agent behaves.
It exists to prevent silent privilege drift and to keep decision authority human-led.

## Core roles

| Role | Responsibility | Typical actions | Cannot do alone |
|---|---|---|---|
| Accountable authority | Final governance authority | Approve high-risk actions, approve scope changes, approve external expansion | Delegate accountability to automation |
| Maintainer or operator | Day-to-day implementation and review | Prepare changes, run validated procedures, collect evidence | Self-approve authority expansion |
| Governed agent | Execute delegated tasks within policy gates | Classify ADAL/CDEL/ESAL/PCL, propose allow/defer/block, produce traceable outputs | Self-grant privilege or redefine authority |

## Human authority is mandatory

The accountable authority remains human.
Automation may support decisions but does not replace authority proof.
If authority is unclear, outcome is defer or block.

## Operational context versus authority proof

Operational context means observed environment state.
Authority proof means explicit approval, delegated scope, and policy alignment.
Context without authority proof is insufficient for risky execution.

## Delegation boundaries

Delegation is bounded by:

- declared objective and scope;
- ADAL/CDEL/ESAL/PCL classification;
- register and procedure prerequisites;
- approval level required for the action class.

Actions outside bounds must be deferred.

## No self-granting principle

A governed agent may not:

- promote its own authority class;
- bypass required approvals;
- reinterpret a block as approval;
- operationalize unknown authority.

Unknown authority defaults to no operational authority.

## Decision outcomes

| Outcome | When used | Required response |
|---|---|---|
| Allow | Scope and authority are confirmed, prerequisites satisfied | Execute with controls and record telemetry |
| Defer | Missing approval, incomplete evidence, or ambiguous classification | Request exact missing evidence or approval |
| Block | Explicit policy violation or prohibited action | Stop execution and report rationale |

## Emergency stop logic

Immediate block and report when any of the following is detected:

- attempted privilege self-granting;
- confidentiality boundary breach;
- missing backup/rollback gate for risky action;
- unknown external target ownership or recovery custody;
- requested action outside approved scope.

## Governance evidence expectations

For authority-sensitive actions, keep evidence concise and reviewable:

- classification summary;
- gate outcomes;
- approvals referenced;
- pre-check and post-check results;
- defer or block rationale when applicable.

Do not include plaintext secrets in evidence artifacts.

## Relationship to other concepts

This model drives:

- ADAL/CDEL/ESAL/PCL classification behavior;
- policy-gate allow/defer/block logic;
- backup and rollback gate enforcement;
- external access governance procedures.

See also:

- [Agent Delegated Administration Level (ADAL)](adal.md)
- [Container Delegated Execution Level (CDEL)](cdel.md)
- [External Service Access Level (ESAL)](esal.md)
- [Project Confidentiality Level (PCL)](pcl.md)
- [Policy Gates](policy-gates.md)
- [Backup and Rollback](backup-and-rollback.md)
