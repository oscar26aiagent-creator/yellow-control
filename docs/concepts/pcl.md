# Project Confidentiality Level (PCL)

PCL defines confidentiality boundaries for project artifacts, governance decisions, and operational evidence.

## Purpose

PCL reduces accidental disclosure risk by forcing explicit publication boundaries before content is shared.

## PCL level table

| Level | Classification | Sharing posture | Typical examples |
|---|---|---|---|
| PCL-0 | Public | Shareable after normal review | Fictional templates and public docs |
| PCL-1 | Internal | Team-limited sharing | Internal process notes without secrets |
| PCL-2 | Private | Restricted to approved operators/authority | Real runtime mappings and access records |
| PCL-3 | Restricted | Strict need-to-know handling | Recovery custody details and sensitive security data |

## Default handling rule

Unknown classification defaults to private handling (PCL-2) until explicitly reclassified.

## Public, private, and restricted examples

| Artifact type | Typical PCL |
|---|---|
| Generic governance template with fictional values | PCL-0 |
| Internal operator checklist | PCL-1 |
| Service inventory with real identities | PCL-2 |
| Break-glass recovery procedure | PCL-3 |

## Publication implications

Before publication, verify:

- source classification,
- allowed audience,
- required redaction,
- approval record for release decision.

If any element is unresolved, defer publication.

## Redaction implications

Redaction must preserve governance meaning while removing identifying details.
A safe redaction keeps policy logic understandable and testable.

## Handling mixed-content artifacts

For mixed public/private content:

- split sensitive details into restricted artifacts,
- keep public docs conceptual,
- use clearly fictional examples,
- record deferred items for unresolved classifications.

## Decision telemetry expectation

Publish/defer/block decisions should record:

- applied classification,
- rationale,
- authority source,
- resulting action.

## Related concepts and procedures

- [Policy gates](policy-gates.md)
- [Project register](../registers/project-register.md)
- [External service register](../registers/external-service-register.md)
- [Secrets handling procedure](../procedures/secrets-handling.md)

Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr
Assisted-by: ChatGPT: GPT-5.5 Thinking; Codex; Hermes Agent v0.13
