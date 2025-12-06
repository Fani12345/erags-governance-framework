---
DocID: ERAGS-PROC-ROOT-001
Title: ERAGS Processes Folder Overview
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
  - ERAGS-DOC-PROC-OV-001
  - ERAGS-DOC-STK-001
  - ERAGS-MOD-PROC-001
  - ERAGS-MOD-PROC-002
  - ERAGS-MOD-PROC-003
  - ERAGS-MOD-CONF-001
  - ERAGS-MOD-CONF-002
  - ERAGS-MOD-CONF-003
RelatedFolders:
  - requirements/
  - models/02_process_models/
  - models/06_configuration_and_metadata_models/
  - qa/
---

# ERAGS Processes Folder Overview

## 1. Purpose

The `processes/` folder contains the **concrete Standard Operating Procedures (SOPs)** that implement the governance, configuration and performance management processes for System 1 – ERAGS.

These SOPs:

- Turn the abstract process models in `models/02_process_models/` into actionable, repeatable procedures.
- Provide auditable, role-based descriptions of how requirements are implemented in practice.
- Are referenced by requirements in `requirements/ERAGS_RTM.csv` (for example as `/processes/*` and by specific PROC IDs such as `PROC-Programme-Governance`).

## 2. Structure

The folder is organised into the following subfolders:

- `00_metadata/`  
  Metadata and conventions for process IDs, naming and linkages.

- `01_governance_core/`  
  Core governance SOPs:
  - Strategy and governance review.
  - Programme governance.
  - Performance and KPI review.
  - Policy management.

- `02_change_and_configuration/`  
  SOPs for:
  - Change control on governance artefacts.
  - Document lifecycle and baseline management.

- `03_data_and_integration/`  
  SOPs for:
  - Data integration from external systems into governance entities.
  - Data quality checks and reconciliation.

- `04_incident_and_risk/`  
  SOPs for:
  - Incident-driven governance intervention.
  - Use of safety and operational incidents at the governance level.

- `05_audit_and_improvement/`  
  SOPs for:
  - Audit preparation and response.
  - Continuous improvement based on audit and performance findings.

## 3. Relationship to Process Models

The abstract process models in `models/02_process_models/` describe **what** the governance flows look like at a conceptual level.

The SOPs in `processes/` describe **how** those flows are carried out in practice, including:

- Inputs and triggers.
- Roles and responsibilities.
- Step-by-step activities.
- Outputs, records and required evidence.

Each SOP will:

- Reference its corresponding model DocID in the YAML front matter.
- Reference relevant requirements IDs and data entities.

## 4. Relationship to Requirements and RTM

The Requirements Traceability Matrix (`requirements/ERAGS_RTM.csv`) refers to `/processes/*` and to specific named processes such as:

- `PROC-Programme-Governance`
- `PROC-Change-Control`
- `PROC-Performance-Management`

For each of these, there is or will be a corresponding SOP under `processes/` with:

- A stable **process DocID** (for example `ERAGS-PROC-002`).
- A human-readable title.
- A file path under the appropriate subfolder.
- Explicit linkages back to the requirements implemented.

## 5. Relationship to Configuration and QA

The SOPs work together with:

- Configuration and metadata models in:
  - `models/06_configuration_and_metadata_models/`
- QA artefacts in:
  - `qa/`

to ensure that:

- Processes are under configuration control and part of baselines.
- QA checks can verify that processes are being followed and that required artefacts are produced.

This folder should be considered part of the formal governance configuration for System 1 – ERAGS.
