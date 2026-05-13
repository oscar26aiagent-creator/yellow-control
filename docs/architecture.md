# Yellow-Control architecture

This document provides public-safe governance architecture views for decision flow, classification, register relationships, and private-to-public extraction safety.

## 1) Governance decision flow

```mermaid
flowchart TD
  A[Action request] --> B[Classify action]
  B --> C[Apply policy gates]
  C --> D{Decision outcome}
  D -->|Allow| E[Execute within approved scope]
  D -->|Defer| F[Request missing authority or evidence]
  D -->|Block| G[Stop action and report]
  E --> H[Emit governance telemetry]
  F --> H
  G --> H
```

## 2) ADAL/CDEL/ESAL/PCL classification flow

```mermaid
flowchart TD
  A[Proposed action] --> B[Classify ADAL]
  B --> C[Classify CDEL]
  C --> D[Classify ESAL]
  D --> E[Classify PCL]
  E --> F{Classification complete?}
  F -->|No| G[Default handling: defer or block]
  F -->|Yes| H[Collect required evidence]
  H --> I[Proceed to policy-gate decision]
```

## 3) Register relationship diagram

```mermaid
flowchart LR
  P[Project register] --> R[Runtime register]
  R --> S[Skill register]
  S --> E[External service register]
  P --> E
  R --> E
```

## 4) Source-to-public extraction safety flow

```mermaid
flowchart TD
  A[Private reference materials] --> B[Public-safe extraction]
  B --> C[Redaction and generalization]
  C --> D[Public documentation draft]
  D --> E[Validation checks]
  E --> F{Pass?}
  F -->|Yes| G[Publish to public repository]
  F -->|No| H[Fix issues and revalidate]
```

Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr
Assisted-by: ChatGPT: GPT-5.5 Thinking; Codex; Hermes Agent v0.13
