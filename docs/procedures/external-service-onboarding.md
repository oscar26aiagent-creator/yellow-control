# External Service Onboarding Procedure

This procedure defines a public-safe onboarding workflow for a new external service.

## Preconditions

- service need is documented,
- ESAL and PCL are classified,
- accountable authority is identified,
- no credentials are embedded in docs.

## Steps

1. Define service purpose and scope.
2. Classify service impact with ESAL.
3. Identify confidentiality requirements with PCL.
4. Validate ownership and recovery custody documentation.
5. Define approved access methods and token scope.
6. Define automation boundaries and approval requirements.
7. Register the service in the external-service register.
8. Record governance decision telemetry.
9. Schedule first audit review.

## Dry-run-first template

Use a dry-run checklist before any live integration:

- classify action,
- verify gate preconditions,
- confirm rollback path,
- confirm no production mutation in dry-run.

## Defer and block conditions

Defer when classification or ownership data is incomplete.
Block when custody, approval, or confidentiality controls are missing.

Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr
Assisted-by: ChatGPT: GPT-5.5 Thinking; Codex; Hermes Agent v0.13
