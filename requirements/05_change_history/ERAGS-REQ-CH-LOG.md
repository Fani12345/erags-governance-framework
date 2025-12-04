---
DocID: ERAGS-REQ-CH-LOG
Title: Requirements Change Log for ERAGS
Version: 0.1
Status: Draft
OwnerRole: Electrical Engineer – Roads Electrical Sub-Section
OwnerName: Fani Masoabi
ApproverRole: Director – Roads Network Maintenance
ApproverName: (to be designated)
CreatedDate: 2025-12-04
LastUpdatedDate: 2025-12-04
System: ERAGS (Electrical Roads Asset Governance & Strategy System)
RelatedDocs:
  - ERAGS-REQ-OV-000
  - ERAGS-REQ-HL-001
RelatedFolders:
  - 06_baselines/
---

# Requirements Change Log for ERAGS

## 1. Purpose

This log records approved changes to ERAGS requirements, including additions, modifications and deletions. It supports traceability and auditability of the evolution of the requirements.

## 2. Change Log Table

| ChangeID | Date       | Requirement_ID(s)      | Description of Change                                      | Reason / Trigger                            | Approved By                  | Baseline Affected |
|---------|------------|------------------------|------------------------------------------------------------|---------------------------------------------|------------------------------|-------------------|
| CH-001  | 2025-12-04 | (initial set)          | Initial creation of ERAGS requirements and RTM structure   | Establish baseline governance requirements  | Director – Roads Network Maintenance (pending) | v0.1-ERAGS-REQ (planned) |

New entries shall be appended to this table with:

- Unique `ChangeID` (for example `CH-002`, `CH-003`).
- Date of approval.
- IDs of affected requirements.
- Summary of the change.
- Reason or trigger (for example new regulation, audit finding, performance issue).
- Approver.
- Baseline impacted or created.

## 3. Relationship to Baselines

For significant changes:

- A new baseline folder shall be created under `requirements/06_baselines/` and/or a Git tag shall be applied.
- The `Baseline Affected` column shall reference the baseline identifier (for example `v0.2-ERAGS-REQ`).

This ensures that requirement states can be reconstructed for any baseline.
