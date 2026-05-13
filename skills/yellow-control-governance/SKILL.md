---
name: yellow-control-governance
description: Governance decision skill for classifying requests and applying policy gates in Hermes-compatible runtimes.
version: 0.1.3
author: F.M. Robert Vergnes
license: MIT
platforms:
  - linux
  - macos
  - windows
metadata:
  hermes:
    tags:
      - governance
      - adal
      - cdel
      - esal
      - pcl
      - policy-gates
      - backup-rollback
      - telemetry
---

# yellow-control-governance

## When to use

Use this skill before actions that may change runtime state, external-service posture, confidentiality, repository safety, or persistent automation.

Activation triggers:

- privileged or high-impact operational requests,
- external-service onboarding or modification,
- publication decisions with mixed confidentiality,
- persistence/automation changes,
- repository actions with governance risk.

## Do not use

Do not use this skill as authority itself.
Do not use this skill to bypass required human approval.
Do not use this skill as a substitute for environment-specific runbooks.

## Required classifications

Every decision must classify the request with:

- ADAL (administration delegation),
- CDEL (container/sandbox delegation),
- ESAL (external-service authority),
- PCL (confidentiality level).

Unknown authority defaults to defer or block.
Unknown confidentiality defaults to private-safe handling.

## Policy-gate behavior

Apply these gates in order:

1. authority gate,
2. scope gate,
3. backup gate,
4. rollback gate,
5. confidentiality gate,
6. external-service gate,
7. repository gate,
8. automation/persistence gate,
9. proposal-only gate.

## Allow / Defer / Block rules

Allow when all required gates pass and evidence is complete.
Defer when scope, authority, or evidence is incomplete.
Block when policy, confidentiality, or safety constraints are violated.

## Output schema

Return a structured result with:

- decision: allow|defer|block
- classifications: {adal, cdel, esal, pcl}
- gate_outcomes: per-gate status and rationale
- required_evidence: missing or validated items
- remediation_actions: next safe actions
- escalation_target: accountable role (if defer/block)
- telemetry_fields: fields to record for audit

## Public-safety constraints

Never include:

- credentials, tokens, recovery artifacts,
- private hostnames/IPs/paths,
- private logs or real register entries,
- endorsement claims of official Hermes/Nous approval.

## References index

- [Skill references index](references/index.md)
- [Policy gates concept](../../docs/concepts/policy-gates.md)
- [Authority model concept](../../docs/concepts/authority-model.md)
- [ADAL concept](../../docs/concepts/adal.md)
- [CDEL concept](../../docs/concepts/cdel.md)
- [ESAL concept](../../docs/concepts/esal.md)
- [PCL concept](../../docs/concepts/pcl.md)
- [Backup and rollback concept](../../docs/concepts/backup-and-rollback.md)

## Safe validation prompt

Classify a proposed change using ADAL/CDEL/ESAL/PCL, apply policy gates, return allow/defer/block with required evidence and remediation actions, and do not execute commands.
