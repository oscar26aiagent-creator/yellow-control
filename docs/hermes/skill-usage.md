# Hermes skill usage for yellow-control-governance

This guide explains how to inspect and use the governance skill in Hermes-compatible runtimes.

## Scope

This document covers usage patterns, validation prompts, and expected output shape.
It does not claim installation commands beyond official Hermes documentation.

Official references:

- https://hermes-agent.nousresearch.com/docs/developer-guide/creating-skills
- https://hermes-agent.nousresearch.com/docs/user-guide/features/skills

## Usage flow

1. Load the skill in a session.
2. Provide action summary and context.
3. Request ADAL/CDEL/ESAL/PCL classification.
4. Request policy-gate decision output.
5. Review allow/defer/block rationale.

## Example validation prompts

- "Classify this change and apply policy gates. Return decision and required evidence. Do not execute commands."
- "Given this external-service change request, return defer/block criteria and escalation target."

## Expected output shape

- decision: allow|defer|block
- classifications: adal/cdel/esal/pcl
- gate_outcomes: authority, scope, backup, rollback, confidentiality, external-service, repository, automation, proposal-only
- required_evidence
- remediation_actions
- escalation_target
- telemetry_fields

## Safety expectations

- no secret material in output,
- no private host or account identifiers,
- no implied official endorsement.

Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr
Assisted-by: ChatGPT: GPT-5.5 Thinking; Codex; Hermes Agent v0.13
