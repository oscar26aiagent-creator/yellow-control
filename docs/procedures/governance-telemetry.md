# Governance Telemetry

Status: v0.1.3 clean architecture rebuild candidate.
Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr

## Purpose

Define minimal decision telemetry for governance actions.
Telemetry must be useful for review while remaining public-safe.

## Required telemetry fields

| Field | Description |
|---|---|
| action_id | Unique identifier for decision event |
| timestamp | Decision time |
| target_id | Target from external access register when relevant |
| classification | ADAL/CDEL/ESAL/PCL summary |
| gate_results | Gate-by-gate allow/defer/block outcomes |
| decision | Final allow, defer, or block |
| evidence_refs | References to validation artifacts |
| reviewer_notes | Concise rationale |

## Telemetry quality rules

- concise and traceable;
- no plaintext secrets;
- no private infrastructure identifiers in public artifacts;
- consistent decision vocabulary.

## Example decision summary format

- Action: update governance concept documentation
- Classification: ADAL-1, CDEL-0, ESAL-3, PCL-0
- Gates: authority allow; scope allow; confidentiality allow
- Decision: allow
- Evidence: commit and validation outputs

## Related documents

- [Policy Gates](../concepts/policy-gates.md)
- [Authority Model](../concepts/authority-model.md)
- [External Access Register](../registers/external-access-register.md)
