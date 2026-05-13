# External Access Register

Status: v0.1.3 clean architecture rebuild candidate.
Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr

## Purpose

This register is the v0.1.3 core register for privileged or external target access governance.
It applies to servers, services, APIs, Git hosting, email systems, cloud dashboards, and identity providers.

## Scope

Use this register before first privileged or external interaction with a target.
Entries define classification, ownership, custody, and allowed action boundaries.

## Field definitions

| Field | Description |
|---|---|
| target_id | Stable unique identifier for the target |
| target_type | Target class such as server, api, git, email, cloud, identity |
| environment | Context such as dev, staging, production |
| hostname | Hostname or endpoint label when applicable |
| ip_address | IP address when applicable |
| port | Network port when applicable |
| access_user | Approved operator account identifier |
| auth_method | Authentication method class |
| ssh_key_ref | Reference to SSH key location, never key material |
| api_key_ref | Reference to API key location, never key material |
| secret_location_ref | Secret storage reference, never plaintext secret |
| external_package_ref | Reference to external package or onboarding artifact |
| adal_level | Required ADAL classification |
| cdel_level | Required CDEL classification |
| esal_level | Required ESAL classification |
| pcl_level | Required PCL confidentiality classification |
| first_contact_status | Not-started, pending, complete, or blocked |
| first_contact_date | Date of first approved contact |
| last_contact_date | Date of most recent interaction |
| last_audited_date | Date of last governance audit |
| last_audit_evidence_ref | Reference to audit evidence artifact |
| allowed_actions | Explicitly allowed action categories |
| forbidden_actions | Explicitly forbidden action categories |
| approval_required | Required approval authority class |
| accountable_authority | Human accountable authority role label |
| operator | Delegated maintainer or operator role label |
| recovery_custody_ref | Recovery ownership reference |
| notes | Public-safe notes only |

## Rules

- No plaintext secrets in register entries.
- Unknown classification defaults to defer.
- Unknown confidentiality defaults to private handling.
- Unregistered privileged external actions are blocked.

## Lifecycle

1. Draft target entry.
2. Validate classifications and custody references.
3. Approve and activate entry.
4. Record first contact status and evidence references.
5. Review periodically and update audit timestamps.

## Relationship to procedures

- [Server First Contact](../procedures/server-first-contact.md)
- [External Access Onboarding](../procedures/external-access-onboarding.md)
- [Secrets Handling](../procedures/secrets-handling.md)
- [Policy Gates](../concepts/policy-gates.md)
