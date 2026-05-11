# External Service Authority Level (ESAL)

ESAL classifies delegated authority for external services such as code hosting, email, cloud APIs, and identity systems.

## Purpose

External services carry custody and recovery risks that differ from local runtime operations.
ESAL makes those risks explicit and auditable before automation or privileged actions occur.

## ESAL level table

| Level | Scope summary | Typical service interaction | Typical posture |
|---|---|---|---|
| ESAL-0 | Public read-only interaction | Read public documentation endpoints | Usually allow |
| ESAL-1 | Authenticated low-impact reads | Read repository metadata with scoped token | Allow with controls |
| ESAL-2 | Controlled bounded writes | Push branch to personal fork | Allow when gates pass |
| ESAL-3 | Organization-impacting operations | Change org-level settings or integrations | Defer pending explicit approval |
| ESAL-4 | Recovery-sensitive authority | Ownership/recovery control operations | Block by default without direct authority |

## Domain examples

| Domain | Typical ESAL concern |
|---|---|
| Git hosting | Branch protections, merge rights, token scope |
| Email service | Confidentiality, mailbox custody, forwarding controls |
| Cloud/API provider | Billing impact, key scope, data exposure surface |
| Identity provider | MFA lifecycle, federation trust, account recovery |

## Ownership and recovery custody

For high-impact service operations, accountable ownership and recovery custody must be documented.
If recovery custody is unclear, high-risk actions should defer or block.

## Access-chain validation

Validate the full access chain before using authority:

1. service identity,
2. account identity and role,
3. token/key scope,
4. approval source,
5. telemetry and audit expectations.

If any link is unresolved, escalation should stop.

## Automation approval requirements

Persistent automation against external services requires:

- explicit approval,
- bounded scope,
- change review cadence,
- revocation path,
- telemetry obligations.

Proposal text alone is not execution authority.

## Escalate, defer, block examples

| Scenario | Decision | Reason |
|---|---|---|
| Push documentation branch to personal fork | Allow | ESAL-2 bounded write |
| Modify organization branch-protection settings | Defer | Organization approval required |
| Change recovery ownership configuration | Block by default | Recovery-custody risk |

## Public-safe constraints

Public docs and examples must exclude:

- real account identifiers,
- private endpoints,
- credential-bearing snippets,
- recovery artifacts.

## Related concepts and registers

- [External service register](../registers/external-service-register.md)
- [Policy gates](policy-gates.md)
- [Project Confidentiality Level (PCL)](pcl.md)
- [Authority model](authority-model.md)

Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr
Assisted-by: ChatGPT: GPT-5.5 Thinking; Codex; Hermes Agent v0.13
