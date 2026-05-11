# GitHub Governance Procedure

This procedure defines safe repository workflow for governed documentation changes.

## Baseline rules

- normal pushes target origin fork branch,
- upstream push requires explicit human instruction,
- branch must be scoped and reviewable.

## Steps

1. Verify remotes and current branch.
2. Confirm scope and milestone boundaries.
3. Commit coherent checkpoint changes.
4. Push to origin branch.
5. Run validation scans.
6. Open review workflow when requested by authority.

## Defer and block conditions

Defer when branch or remotes are ambiguous.
Block when change requests require upstream mutation without explicit instruction.

## Safety constraints

- no secret material in commits,
- no private operational identifiers in public docs,
- no destructive history rewrites without explicit approval.

Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr
Assisted-by: ChatGPT: GPT-5.5 Thinking; Codex; Hermes Agent v0.13
