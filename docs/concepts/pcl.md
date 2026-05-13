# Project Confidentiality Level (PCL)

Status: v0.1.3 clean architecture rebuild candidate.
Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr

## Purpose

PCL classifies information disclosure boundaries for project artifacts and governance evidence.
It defines what may be public, restricted, or private.

## Default rule

If confidentiality classification is unknown, default to private handling.
No publication occurs until classification is explicit.

## PCL level table

| Level | Meaning | Typical content | Publication default |
|---|---|---|---|
| PCL-0 | Public-safe by design | Generic governance templates and examples | Publish allowed |
| PCL-1 | Public with review | Non-sensitive operational summaries | Publish after review |
| PCL-2 | Private operational | Internal runbooks and sensitive operational context | Do not publish |
| PCL-3 | Restricted sensitive | Security-sensitive details with high misuse risk | Strictly restricted |
| PCL-4 | Critical confidential | Recovery/ownership control data and sensitive secrets context | Never public |

## Public, private, restricted examples

| Example | Suggested PCL |
|---|---|
| Generic policy-gate explanation | PCL-0 |
| Fictional register sample | PCL-0 |
| Environment-specific security workflow notes | PCL-2 |
| Identity recovery process specifics | PCL-3 or PCL-4 |

## Publication implications

Before publication:

- confirm PCL classification;
- remove environment-specific sensitive identifiers;
- preserve governance intent while generalizing implementation details.

## Redaction implications

Redaction must not break policy meaning.
Safe redaction removes sensitive identifiers while preserving decision logic and control requirements.

## Defer and block conditions

Defer publication when classification is uncertain.
Block publication when content contains restricted or critical confidential material.

## Relationship to other concepts

PCL interacts with ADAL/CDEL/ESAL because authority decisions often reference confidential evidence.
Confidential evidence can support governance decisions without being publicly disclosed.

## Classification workflow

Use this quick workflow before sharing any artifact:

1. Identify audience and intended channel.
2. Classify content at draft time, not only at publication time.
3. Remove or generalize sensitive identifiers where possible.
4. Re-check references and embedded snippets for confidentiality drift.
5. Record final PCL decision in review notes.

## Common mistakes to avoid

- Treating unknown confidentiality as public-safe.
- Publishing operational evidence without reclassification.
- Mixing public examples with private environment details.
- Assuming redaction is complete without a second pass.

## Related documentation

- [Authority Model](authority-model.md)
- [Policy Gates](policy-gates.md)
- [Secrets Handling](../procedures/secrets-handling.md)
- [External Access Register](../registers/external-access-register.md)
