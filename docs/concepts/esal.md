# External Service Access Level (ESAL)

Status: v0.1.3 clean architecture rebuild candidate.
Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr

## Purpose

ESAL classifies delegated authority for external services and remote control planes.
It applies to Git hosting, email, cloud APIs, dashboards, identity providers, and similar systems.

## Why ESAL exists

External access can carry high blast radius and recovery risk.
ESAL ensures authority, custody, and approval are explicit before action.

## ESAL level table

| Level | Meaning | Typical examples | Default decision |
|---|---|---|---|
| ESAL-0 | No external interaction | Offline documentation work | Allow |
| ESAL-1 | Public-read external lookup | Public repository metadata checks | Allow |
| ESAL-2 | Low-risk authenticated read | Read-only API queries | Allow with logging |
| ESAL-3 | Scoped write operations | Branch pushes to owned fork, issue updates | Defer if scope unclear |
| ESAL-4 | High-impact operational writes | Production configuration changes | Defer by default |
| ESAL-5 | Ownership and recovery authority | Billing, account ownership, recovery controls | Block without explicit authority |

## Target classes

ESAL applies across target types:

- Git platforms;
- email systems;
- cloud and API providers;
- identity and access dashboards;
- external management portals.

## Ownership and recovery custody

Before ESAL-4/5 actions, confirm who owns recovery and break-glass controls.
Unknown recovery custody is a hard defer or block condition.

## Access-chain validation

Validate chain-of-access before acting:

- target identity is registered;
- operator identity is approved for target class;
- credential reference exists (not plaintext);
- approval scope matches requested operation.

## Automation approval requirements

Automated external writes require explicit governance approval and traceability.
No autonomous escalation from read to write is allowed.

## Escalation, defer, and block examples

| Scenario | ESAL view | Outcome |
|---|---|---|
| Read public repository metadata | ESAL-1 | Allow |
| Push documentation branch to owned fork | ESAL-3 | Allow with branch scope |
| Modify production cloud policy without approval | ESAL-4 | Defer |
| Change account recovery ownership without explicit authority | ESAL-5 | Block |

## Relationship to external access register

External targets must be represented in the external access register before privileged use.
Register entries should reference secret locations, not include plaintext secrets.

See:

- [External Access Register](../registers/external-access-register.md)
- [External Access Onboarding](../procedures/external-access-onboarding.md)
- [Server First Contact](../procedures/server-first-contact.md)
- [Policy Gates](policy-gates.md)
