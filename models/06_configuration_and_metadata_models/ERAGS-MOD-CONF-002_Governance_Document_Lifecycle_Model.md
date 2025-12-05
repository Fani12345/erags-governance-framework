---
DocID: ERAGS-MOD-CONF-002
Title: ERAGS Governance Document Lifecycle Model
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
  - ERAGS-DOC-OV-000
  - ERAGS-DOC-PROC-OV-001
  - ERAGS-MOD-DATA-003
  - ERAGS-MOD-CONF-001
RelatedFolders:
  - docs/
  - requirements/
  - models/
---

# ERAGS Governance Document Lifecycle Model

## 1. Purpose

This document defines the lifecycle of governance documents in ERAGS:

- States a document can be in.
- Transitions between states.
- Roles responsible for each state transition.

It ensures:

- Controlled evolution of policies, strategies, requirements and models.
- Clear separation between drafts and approved artefacts.
- Auditability of document changes.

It elaborates ERAGS-F-009 and ERAGS-R-003.

## 2. Lifecycle States

Standard lifecycle states:

1. **Draft**
   - Document is under preparation or internal refinement.
   - Content can change frequently.
   - Not yet authorised for use as a governance reference.

2. **UnderReview**
   - Document is being reviewed by relevant stakeholders.
   - Changes are more controlled; comments and requested changes are tracked.

3. **Approved**
   - Document has been formally approved by the designated approver role.
   - Forms part of the current governance baseline(s).

4. **Superseded**
   - Document has been replaced by a newer version.
   - Kept for historical reference, but not used for current decisions.

5. **Archived**
   - Document is retained for historical/legal reasons only.
   - Not active in any current governance baseline.

These states correspond to values in the `Status` field in GovernanceDocumentMetadata (see ERAGS-MOD-DATA-003).

## 3. Lifecycle Transitions

Typical transitions:

- Draft → UnderReview  
- UnderReview → Approved  
- Approved → Superseded  
- Superseded → Archived  

Some transitions may be constrained:

- Draft → Approved should normally occur only via UnderReview.
- Approved → Draft is not allowed; instead a new version begins as Draft.

Each transition should be triggered via a governance process step (for example review meeting, approval decision).

## 4. Roles and Responsibilities

- **Author / OwnerRole**
  - Responsible for producing and maintaining content.
  - Initiates Draft and proposes transitions to UnderReview.

- **Reviewer(s)**
  - Provide comments and recommendations.
  - May request revisions before advancing to Approved.

- **ApproverRole**
  - Has authority to approve documents.
  - Records approval date and changes Status to Approved.

- **Configuration Manager / Document Controller**
  - Ensures document metadata is consistent and complete.
  - Updates baselines when new Approved versions replace older ones.
  - Manages Archiving.

## 5. Versioning Rules

- Each document has a `Version` field (for example 0.1, 0.2, 1.0, 1.1).
- Informal rule:
  - 0.x: Draft versions.
  - 1.0: First approved version.
  - 1.x: Approved versions with minor changes.
  - 2.0, 3.0, etc.: Major revisions.

Version changes should coincide with important lifecycle transitions or significant changes in content.

## 6. Relationship with Git and Baselines

- Document lifecycle is independent of Git, but they complement each other:
  - Approved versions should be associated with Git commits and, where relevant, Git tags (for baselines).
  - Superseded documents remain in Git history and/or in special Archive folders.

- Baselines (see ERAGS-MOD-CONF-001) should reference:
  - Specific versions and states (usually Approved) of documents.

## 7. Lifecycle Control in Practice

For each key governance document:

1. Author creates initial Draft with metadata including:
   - DocID, Title, Version (0.1), Status (Draft).

2. When content is ready for review:
   - OwnerRole initiates a governance review process (as defined in process models).
   - Status changes to UnderReview.

3. Following review and any required changes:
   - ApproverRole approves the document.
   - Status set to Approved.
   - Version updated (for example from 0.3 to 1.0).

4. When a new revision is needed:
   - A new version begins as Draft (for example 1.1 or 2.0).
   - Older version remains Approved until superseded.

5. Once a document is no longer applicable:
   - Status set to Superseded or Archived.
   - Baseline definitions are updated accordingly.

## 8. Traceability and Audit

- Every change of Status should be linked to:
  - A decision record (DecisionLogEntry).
  - A specific commit in Git when possible.

Auditors can:

- Trace from the current baseline to the Approved version of each document.
- Trace from that version back to decision records supporting its approval.

