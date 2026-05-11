# Skill Register

This register defines the public-safe schema for governance skill inventory metadata.
It does not grant authority by itself.

## Required fields

| Field | Description |
|---|---|
| skill_name | Canonical skill identifier |
| purpose | Concise governance purpose |
| risk_class | Risk category for skill use |
| dependencies | Required docs, tools, or runtime capabilities |
| external_services | Referenced external services, if any |
| required_approval | Approval requirement before risky operations |
| telemetry_required | Required decision/execution telemetry |
| references | Canonical references index |

## Governance expectations

Skill capability does not equal authority.
Approval and policy gates still apply.

## Fictional example entry

```yaml
skill_name: "yellow-control-governance"
purpose: "classify actions and enforce policy-gate decisions"
risk_class: "medium"
dependencies:
  - "docs/concepts/policy-gates.md"
external_services: []
required_approval: "required for privileged or persistent automation actions"
telemetry_required: true
references:
  - "skills/yellow-control-governance/references/index.md"
```

## Related documents

- [Policy gates](../concepts/policy-gates.md)
- [Skill usage](../hermes/skill-usage.md)
- [Skill references index](../../skills/yellow-control-governance/references/index.md)

Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr
Assisted-by: ChatGPT: GPT-5.5 Thinking; Codex; Hermes Agent v0.13
