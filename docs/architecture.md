# Architecture

Status: v0.1.3 clean architecture rebuild candidate.
Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr

This architecture describes Yellow-Control core governance only.
External package management can be referenced as a separate layer, not merged into core doctrine.

## Core governance flow

```mermaid
flowchart TD
  A[Action request] --> B[Classify ADAL CDEL ESAL PCL]
  B --> C[Apply policy gates]
  C --> D{Allow Defer Block}
  D --> E[Governed execution or governance response]
  E --> F[Telemetry and evidence references]
```

## Classification and scope

```mermaid
flowchart TD
  A[Action candidate] --> B[Classify ADAL]
  A --> C[Classify CDEL]
  A --> D[Classify ESAL]
  A --> E[Classify PCL]
  B --> F[Scope and authority evaluation]
  C --> F
  D --> F
  E --> F
  F --> G{Known and approved}
  G -->|Yes| H[Allow path]
  G -->|Partial| I[Defer path]
  G -->|No| J[Block path]
```

## Register and procedure relationship

```mermaid
flowchart LR
  A[External access register] --> B[Server first contact]
  A --> C[External access onboarding]
  A --> D[GitHub governance]
  A --> E[Secrets handling]
  B --> F[Governance telemetry]
  C --> F
  D --> F
  E --> F
```

## Boundary with external package management

```mermaid
flowchart TD
  A[Yellow-Control core docs and skill] --> B[Policy decisions and gates]
  C[External package management layer] --> D[Implementation-specific artifacts]
  B --> E[Reference external package only when needed]
  D --> E
  E --> F[No private implementation details in public core docs]
```
