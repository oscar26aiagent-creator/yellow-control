---
name: yellow-control-governance
description: Public-safe governance skill for authority classification, policy gates, and external access controls.
version: 0.1.3
author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr
license: MIT
platforms:
  - linux
metadata:
  hermes:
    tags:
      - governance
      - adal
      - cdel
      - esal
      - pcl
      - external-access
      - allow-defer-block
---

# yellow-control-governance

## When to use

Use this skill when actions involve privileged authority, external services, confidentiality decisions, backup/rollback gates, or governance decision reporting.

## Do not use

Do not use this skill as a deployment script, runtime installer, or substitute for human accountable authority.

## Required classification

Before deciding, classify action context using ADAL, CDEL, ESAL, and PCL.
Unknown classification defaults to defer.

## Core behavior

1. Classify ADAL/CDEL/ESAL/PCL.
2. Consult external access register before external or server work.
3. Enforce server-first-contact procedure for first privileged contact.
4. Enforce backup/rollback gate for risky actions.
5. Return allow, defer, or block with concise rationale.
6. Never self-grant authority and never expose secrets.

## Output schema

- decision: allow | defer | block
- classifications: { adal, cdel, esal, pcl }
- gates: { authority, scope, backup_rollback, external_access, confidentiality, automation_persistence }
- evidence_refs: []
- rationale: string
- next_actions: []

## Defer and block rules

Defer when approval, classification, or required evidence is incomplete.
Block when action violates explicit governance boundaries or confidentiality constraints.

## References

- references/index.md
- ../../docs/concepts/authority-model.md
- ../../docs/concepts/policy-gates.md
- ../../docs/registers/external-access-register.md
- ../../docs/procedures/server-first-contact.md
