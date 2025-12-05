---
DocID: ERAGS-MOD-CONF-001
Title: ERAGS Configuration Item and Baseline Model
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
  - ERAGS-MOD-ARCH-002
  - ERAGS-MOD-PROC-002
  - ERAGS-MOD-PROC-003
RelatedFolders:
  - docs/
  - requirements/
  - models/
  - qa/
---

# ERAGS Configuration Item and Baseline Model

## 1. Purpose

This document defines:

- What constitutes a **Configuration Item (CI)** in ERAGS.
- How CIs are grouped into **baselines**.
- How baselines are used to support traceability, audits, and controlled change.

It implements configuration-related aspects of:

- ERAGS-F-005 – Requirements and Traceability Management.
- ERAGS-F-009 – Documentation Control.
- ERAGS-R-003 – Documentation and Auditability.
- ERAGS-NF-002, ERAGS-NF-003 – Traceability and maintainability.

## 2. Configuration Item Types

ERAGS treats the following governance artefacts as CIs:

1. **Governance Documents**
   - Policies, strategies, context descriptions, process overviews.
   - Located mainly in `docs/`.
   - Represented by GovernanceDocumentMetadata (see ERAGS-MOD-DATA-003).

2. **Requirements and RTM**
   - Requirements overviews, detailed requirement specs, the RTM.
   - Located in `requirements/`.

3. **Models**
   - Architecture, process, data, information flow, KPI and configuration models.
   - Located in `models/**`.

4. **QA Artefacts**
   - QA plans, checklists, scripts descriptions.
   - Located in `qa/`.

5. **Reference Data Samples**
   - Example CSVs, dictionaries used for demonstrations or tests.
   - Located in `data/` (if used for baselining).

Code, scripts and diagrams generated from this repository may also be treated as CIs if explicitly brought under configuration control.

## 3. CI Identification

Each CI is uniquely identified by:

- **DocID** (for Markdown artefacts with front matter).
- **Path** (relative repository path).
- **Version** (as recorded in front matter).

For example:

- CI: `ERAGS-DOC-POL-001`  
  - Type: Policy document  
  - Path: `docs/ERAGS-DOC-POL-001_Policy_Framework.md`  
  - Version: `1.0`  

CI metadata is aligned with the GovernanceDocumentMetadata entity in `ERAGS-MOD-DATA-003`.

## 4. Baselines

### 4.1 Baseline Definition

A **baseline** is a named, controlled snapshot of a related set of CIs at specific versions, used as a reference for:

- Reviews.
- Audits.
- Governance cycles (for example strategy review cycle, programme approval cycle).

Each baseline is described by:

- BaselineID
- Name
- Purpose
- DateCreated
- Scope (which CIs are included)
- OwnerRole / ApproverRole
- Related governance cycle or decision

### 4.2 Example Baselines

1. **ERAGS-BL-REQ-001 – Requirements Definition Baseline**
   - Content:
     - `ERAGS-REQ-OV-000`, `ERAGS-REQ-HL-001`, detailed requirement specs.
     - `ERAGS_RTM.csv`.
   - Purpose:
     - Freeze requirements for a given development iteration of ERAGS.

2. **ERAGS-BL-GOV-001 – Governance Framework Baseline**
   - Content:
     - Key docs: context, policy, strategy, process overview.
     - Architecture models: context, logical, component responsibilities.
     - Process models: context/stakeholder, policy management, programme governance.
   - Purpose:
     - Provide a stable governance framework reference for audits and external review.

3. **ERAGS-BL-PERF-001 – Performance and KPI Baseline**
   - Content:
     - KPI definitions and structure.
     - KPI calculation and data lineage.
     - Decision rules and thresholds.
   - Purpose:
     - Allow comparison of performance across periods under consistent KPI definitions.

## 5. Baseline Representation

Baselines may be represented in:

- Markdown summary documents under `models/06_configuration_and_metadata_models/` (for example `ERAGS-CONF-BL-001_Requirements_Baseline_Description.md` at a later stage).
- Git tags and/or Git branches carrying the BaselineID in their names.

Example Git tag naming convention:

- `baseline/ERAGS-BL-REQ-001`
- `baseline/ERAGS-BL-GOV-001`

## 6. Relationship to Git

At repository level:

- Each baseline corresponds to:
  - A **tag** at a specific commit, and/or
  - A **long-lived branch** if further work is planned from that baseline.
- The CI and baseline model does not depend on any specific Git workflow, but:
  - Tagging and branching should follow a documented convention.
  - Tags should include BaselineID and short description.

## 7. Change Control

- Changes to CIs that belong to an approved baseline should:
  - Be proposed through a change control process (see PROC-Change-Control).
  - Include impact analysis on related CIs (requirements, models, KPIs, decision rules).
- A new baseline may be created when:
  - A set of changes has been approved and implemented.
  - A formal review cycle is completed.

## 8. Traceability

- The RTM (`ERAGS_RTM.csv`) links requirements to implementing CIs.
- This configuration model links CIs and baselines to:
  - Governance processes.
  - Decisions (DecisionLogEntry).

It supports end-to-end traceability from requirements, through implementation, to baselined artefacts and decisions.

## 9. Relationship to Other Models

- Uses metadata fields defined in `ERAGS-MOD-DATA-003`.
- Supports:
  - `ERAGS-MOD-CONF-002_Governance_Document_Lifecycle_Model.md`.
  - QA checks for completeness and consistency of CI identification and baselines.
