---
DocID: ERAGS-MOD-CONF-003
Title: ERAGS Repository Metadata and Git Workflow Model
Version: 0.1
Status: Draft
OwnerRole: Electrical Engineer – Roads Electrical Sub-Section
OwnerName: Fani Masoabi
ApproverRole: Director – Roads Network Maintenance
ApproverName: (to be designated)
CreatedDate: 2025-12-05
LastUpdatedDate: 2025-12-05
System: ERAGS (Electrical Roads Asset Governance & Strategy System)
RelatedDocs:
  - ERAGS-MOD-CONF-001
  - ERAGS-MOD-CONF-002
  - ERAGS-MOD-DATA-003
RelatedFolders:
  - .
  - docs/
  - requirements/
  - models/
  - qa/
---

# ERAGS Repository Metadata and Git Workflow Model

## 1. Purpose

This document describes:

- How repository-level metadata (branches, tags, commit messages) supports ERAGS configuration management.
- A simple Git workflow suitable for a governance and documentation-heavy system.

It links the conceptual configuration model to practical Git usage in Visual Studio Code.

## 2. Branching Model

A simple branching model is adopted:

- **main**
  - Always contains the latest stable configuration of ERAGS artefacts.
  - Suitable to present to reviewers and for baselines.

- **feature/\*** branches
  - Used for developing specific changes (for example `feature/kpi-models`, `feature/qa-checks`).
  - Merged into `main` once completed and reviewed.

Optional:

- **hotfix/\*** branches for urgent corrections to `main` after a baseline.

## 3. Tagging Model

Tags are used to:

- Mark **baselines**, using names like:
  - `baseline/ERAGS-BL-REQ-001`
  - `baseline/ERAGS-BL-GOV-001`
- Mark important milestones (for example first complete System 1 governance baseline).

Each tag should be associated with:

- A short description in the tag message.
- A corresponding baseline description in a Markdown file (if the baseline is formal).

## 4. Commit Message Conventions

Commit messages should be:

- Short but descriptive.
- Reference the main change and, if relevant, related requirement IDs.

Examples:

- `Add ERAGS governance data models and update RTM`
- `Define KPI decision rules and link to RTM`
- `Create ERAGS configuration and lifecycle models`

This supports traceability and quick navigation through history.

## 5. Repository Metadata Fields

Repository-wide metadata includes:

- Project name and purpose (documented in `README.md` at root).
- System name and scope (ERAGS; System 1).
- References to higher-level system context (NRE²OS).

This file and `README.md` together ensure that reviewers can understand:

- What the repository represents.
- How it is structured.
- How to navigate it.

## 6. Relationship to Document Metadata

- Every governance document has front-matter metadata (DocID, Version, Status, etc.).
- Git provides temporal and change-oriented metadata (who changed what, and when).
- Together they provide:
  - State-based view (document lifecycle).
  - History-based view (Git commit history).

Both should be used in audits and reviews.

## 7. Practical Workflow Summary

A typical workflow for System 1 – ERAGS work:

1. Start from `main` (updated from remote).
2. Create a feature branch for a cluster of changes:
   - `git checkout -b feature/kpi-models`
3. Make changes in `docs/`, `requirements/`, `models/`, `qa/`.
4. Commit frequently with clear messages.
5. After completing a coherent unit of work:
   - Merge the feature branch into `main`.
6. When a significant stable state is reached:
   - Create a baseline description document (if needed).
   - Tag the commit with a baseline tag (`baseline/ERAGS-BL-XXX`).

This model is intentionally simple so that the focus remains on governance content rather than complex Git workflows.

