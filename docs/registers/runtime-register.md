# Runtime Register

This register defines the public-safe schema for runtime governance posture.
Use fictional examples only in public repositories.

## Required fields

| Field | Description |
|---|---|
| runtime_id | Runtime identifier |
| runtime_class | Runtime category (local, containerized, managed, other) |
| adal_baseline | Baseline ADAL authority model |
| cdel_baseline | Baseline CDEL boundary model |
| backup_status | Backup/checkpoint readiness summary |
| maintenance_cadence | Planned governance maintenance cadence |
| approval_model | Human approval model for high-impact changes |

## Governance expectations

Runtime capabilities do not replace authority proof.
Backup and rollback readiness are preconditions for high-impact changes.

## Fictional example entry

```yaml
runtime_id: "runtime-example-dev"
runtime_class: "local"
adal_baseline: "ADAL-1"
cdel_baseline: "CDEL-1"
backup_status: "checkpoint-required-before-runtime-change"
maintenance_cadence: "weekly"
approval_model: "human-approval-required-for-privileged-actions"
```

## Related documents

- [ADAL concept](../concepts/adal.md)
- [CDEL concept](../concepts/cdel.md)
- [Backup and rollback](../concepts/backup-and-rollback.md)

Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr
Assisted-by: ChatGPT: GPT-5.5 Thinking; Codex; Hermes Agent v0.13
