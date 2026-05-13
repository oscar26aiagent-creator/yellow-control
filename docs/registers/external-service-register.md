# External Service Register

This register defines the public-safe schema for governing external services.
Use fictional examples in public repositories.

## Purpose

The external service register captures authority, custody, and review metadata for service usage.
It supports ESAL classification and policy-gate decisions.

## Required fields

| Field | Description |
|---|---|
| service_name | Canonical service identifier used in governance docs |
| service_type | Service category (code hosting, email, cloud API, identity, other) |
| esal_level | External Service Authority Level classification |
| accountable_authority | Human authority accountable for service decisions |
| maintainer_operator | Role responsible for approved operational execution |
| access_method | Approved access path (interactive, token, API key, OAuth, etc.) |
| recovery_custody_status | Whether recovery custody is documented and valid |
| automation_allowed | Whether persistent automation is approved for this service |
| approval_required | Conditions requiring explicit approval before action |
| audit_cadence | Review frequency for authority and access metadata |
| public_private_notes | Classification notes and publication constraints |
| last_reviewed | Date of latest governance review |

## Ownership and authority notes

- authority decisions remain human-accountable,
- execution remains scope-bound,
- recovery-sensitive operations default to block without explicit authority.

## Approval and audit cadence guidance

Use monthly or quarterly cadence for high-impact services.
Use immediate review after ownership, token-scope, or policy changes.

## Fictional example entry

```yaml
service_name: "example-code-host"
service_type: "code-hosting"
esal_level: "ESAL-2"
accountable_authority: "governance-owner@example.invalid"
maintainer_operator: "platform-maintainer@example.invalid"
access_method: "ssh-key + scoped token"
recovery_custody_status: "documented"
automation_allowed: true
approval_required: "required for org-level settings changes"
audit_cadence: "monthly"
public_private_notes: "fictional sample; no real account data"
last_reviewed: "2026-05-11"
```

## Related documents

- [ESAL concept](../concepts/esal.md)
- [Policy gates](../concepts/policy-gates.md)
- [Project register](project-register.md)
- [Skill register](skill-register.md)

Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr
Assisted-by: ChatGPT: GPT-5.5 Thinking; Codex; Hermes Agent v0.13
