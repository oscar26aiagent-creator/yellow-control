# Secrets Handling

Status: v0.1.3 clean architecture rebuild candidate.
Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr

## Purpose

Define public-safe and operational-safe handling rules for secret material references.

## Core rules

- Never commit plaintext secrets.
- Never print secret values in reports.
- Use reference fields for secret locations.
- Restrict secret access to approved operators.

## Register usage

External access entries may include:

- ssh_key_ref
- api_key_ref
- secret_location_ref

These are references only.

## Safe patterns

| Pattern | Allowed |
|---|---|
| Vault reference identifier | Yes |
| Redacted token prefix with context only | Yes, if policy allows |
| Plaintext token, password, private key | No |

## Incident handling

If a secret leak is suspected:

1. stop dissemination;
2. rotate or revoke affected credentials through approved authority;
3. record incident summary without exposing secret value;
4. update governance notes and corrective actions.

## Related documents

- [External Access Register](../registers/external-access-register.md)
- [Policy Gates](../concepts/policy-gates.md)
