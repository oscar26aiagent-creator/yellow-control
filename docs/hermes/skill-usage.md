# Skill Usage

Status: v0.1.3 clean architecture rebuild candidate.
Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr

## Purpose

Explain how to inspect and use the Yellow-Control governance skill in Hermes-compatible runtimes.

## Basic usage pattern

1. Load and inspect the skill.
2. Provide action context.
3. Require ADAL/CDEL/ESAL/PCL classification.
4. Require allow/defer/block output with gate rationale.

## Example validation prompts

- Classify this action and return allow/defer/block with gate outcomes.
- Evaluate first-contact request for a new external server target.
- Check whether backup/rollback gate is satisfied before risky change.

## Expected output shape

- decision
- classifications
- gate_results
- evidence_refs
- rationale
- next_actions

## Notes

This documentation avoids untested installation claims.
Use current Hermes documentation for runtime-specific install and configuration steps.
