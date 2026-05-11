# Runtime Maintenance Governance Procedure

This procedure governs runtime maintenance actions with checkpoint discipline.

## Preconditions

- change objective is defined,
- ADAL/CDEL classification is recorded,
- backup and rollback gates pass,
- approval evidence exists for privileged scope.

## Steps

1. Classify maintenance action.
2. Validate policy gates.
3. Capture pre-change checkpoint evidence.
4. Execute approved bounded action.
5. Run post-change validation checks.
6. Record telemetry and outcomes.
7. Trigger rollback if validation fails.

## Dry-run-first guidance

Where possible, execute check-only paths first.
Do not run destructive operations during dry-run.

## Stop conditions

Stop immediately on authority mismatch, failed checkpoint gate, or confidentiality violation.

Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr
Assisted-by: ChatGPT: GPT-5.5 Thinking; Codex; Hermes Agent v0.13
