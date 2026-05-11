# Project Register

This register defines a public-safe schema for project governance metadata.
Use fictional values in published examples.

## Required fields

| Field | Description |
|---|---|
| project_id | Stable project identifier |
| project_name | Human-readable project name |
| pcl_level | Project Confidentiality Level classification |
| owner_operator | Accountable owner/operator role |
| allowed_repos | Approved repository targets for work |
| allowed_external_services | Approved service dependencies by canonical name |
| automation_allowed | Whether persistent automation is approved |
| publication_allowed | Whether publication is allowed under current classification |
| review_cadence | Expected review cadence for project governance |

## Governance expectations

Unknown confidentiality defaults to private handling.
Unknown authority defaults to no operational authority.

## Fictional example entry

```yaml
project_id: "proj-example-governance"
project_name: "Example Governance Project"
pcl_level: "PCL-0"
owner_operator: "project-owner@example.invalid"
allowed_repos:
  - "git@example.invalid:team/example-governance.git"
allowed_external_services:
  - "example-code-host"
automation_allowed: false
publication_allowed: true
review_cadence: "monthly"
```

## Related documents

- [PCL concept](../concepts/pcl.md)
- [Authority model](../concepts/authority-model.md)
- [Runtime register](runtime-register.md)

Author: F.M. Robert Vergnes / robert.vergnes@yahoo.fr
Assisted-by: ChatGPT: GPT-5.5 Thinking; Codex; Hermes Agent v0.13
