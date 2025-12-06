---
DocID: ERAGS-PROC-META-001
Title: ERAGS Process IDs and Conventions
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
  - processes/
  - models/02_process_models/
  - models/06_configuration_and_metadata_models/
---

# ERAGS Process IDs and Conventions

## 1. Purpose

This document defines:

- The naming and identification conventions for ERAGS governance processes.
- The mapping between **process IDs (ERAGS-PROC-xxx)**, file paths under `processes/`, and abstract process models under `models/02_process_models/`.
- How processes relate to stakeholder roles and requirements.

It provides a single reference for anyone navigating the `processes/` folder.

## 2. Process ID Convention

Each concrete process is given a unique **DocID** of the form:

- `ERAGS-PROC-###_Short_Descriptive_Name`

where:

- `###` is a three-digit sequence number (for example 001, 002, 003).
- The short descriptive name is a concise indication of the process purpose.

These DocIDs are used:

- In YAML front matter of process SOPs under `processes/`.
- In references from:
  - `requirements/ERAGS_RTM.csv`
  - Process models (for example ERAGS-MOD-PROC-002)
  - Configuration and QA artefacts.

## 3. Index of Defined Processes

The table below lists the core processes currently defined for System 1 – ERAGS.

| Proc DocID        | File Path                                                                 | Short Name                             | Purpose Summary                                                                                     | Related Models                                                                                                     | Key Requirements (Examples)                    |
|-------------------|---------------------------------------------------------------------------|----------------------------------------|-----------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------|------------------------------------------------|
| ERAGS-PROC-001    | processes/01_governance_core/ERAGS-PROC-001_Strategy_and_Governance_Review_Process.md | Strategy and Governance Review         | Periodic governance review of performance, risk and strategy; triggers programme and policy actions | ERAGS-MOD-PROC-001; ERAGS-MOD-PROC-003; ERAGS-MOD-FLOW-002                                                         | ERAGS-F-002; ERAGS-F-003; ERAGS-F-008; ERAGS-NF-006 |
| ERAGS-PROC-002    | processes/01_governance_core/ERAGS-PROC-002_Programme_Governance_SOP.md  | Programme Governance                   | End-to-end governance of investment and renewal programmes                                          | ERAGS-MOD-PROC-003; ERAGS-MOD-ARCH-002; ERAGS-MOD-FLOW-001; ERAGS-MOD-FLOW-002                                    | ERAGS-F-002; ERAGS-F-006; ERAGS-D-001          |
| ERAGS-PROC-003    | processes/01_governance_core/ERAGS-PROC-003_Performance_and_KPI_Review_SOP.md | Performance and KPI Review             | Regular review of KPIRecord and PerformanceSummary, applying thresholds and decision rules         | ERAGS-MOD-KPI-001; ERAGS-MOD-KPI-002; ERAGS-MOD-KPI-003; ERAGS-MOD-FLOW-001; ERAGS-MOD-FLOW-002                   | ERAGS-F-008; ERAGS-D-002; ERAGS-D-003; ERAGS-NF-006 |
| ERAGS-PROC-004    | processes/01_governance_core/ERAGS-PROC-004_Policy_Management_SOP.md     | Policy Management                      | Governance process for drafting, reviewing, approving and retiring policies                         | ERAGS-MOD-PROC-002; ERAGS-MOD-DATA-003; ERAGS-MOD-CONF-002                                                         | ERAGS-F-001; ERAGS-F-009; ERAGS-R-002          |
| ERAGS-PROC-005    | processes/02_change_and_configuration/ERAGS-PROC-005_Change_Control_SOP.md | Change Control                         | Control of changes to policies, strategies, requirements, models and KPIs                           | ERAGS-MOD-CONF-001; ERAGS-MOD-CONF-002; ERAGS-MOD-CONF-003                                                         | ERAGS-F-007; ERAGS-F-009; ERAGS-R-003          |
| ERAGS-PROC-006    | processes/02_change_and_configuration/ERAGS-PROC-006_Document_Lifecycle_and_Baseline_Management_SOP.md | Document Lifecycle and Baselines       | Management of document states (Draft, UnderReview, Approved, etc.) and configuration baselines     | ERAGS-MOD-CONF-001; ERAGS-MOD-CONF-002; ERAGS-MOD-CONF-003; ERAGS-MOD-DATA-003                                     | ERAGS-F-009; ERAGS-D-004; ERAGS-R-003          |
| ERAGS-PROC-007    | processes/03_data_and_integration/ERAGS-PROC-007_Data_Integration_and_Quality_Checks_SOP.md | Data Integration and Quality Checks    | Integration of data from external systems into governance entities; data quality controls           | ERAGS-MOD-DATA-001; ERAGS-MOD-DATA-002; ERAGS-MOD-FLOW-001; ERAGS-MOD-KPI-002                                      | ERAGS-D-001; ERAGS-D-002; ERAGS-D-003; ERAGS-NF-002 |
| ERAGS-PROC-008    | processes/04_incident_and_risk/ERAGS-PROC-008_Incident_Driven_Governance_Intervention_SOP.md | Incident-Driven Governance Intervention | Governance response when serious incidents or critical KPI deviations occur                        | ERAGS-MOD-FLOW-001; ERAGS-MOD-FLOW-002; ERAGS-MOD-KPI-003                                                          | ERAGS-D-002; ERAGS-D-003; ERAGS-R-001; ERAGS-R-003 |
| ERAGS-PROC-009    | processes/05_audit_and_improvement/ERAGS-PROC-009_Audit_and_Continuous_Improvement_SOP.md | Audit and Continuous Improvement       | Handling of audits and use of audit findings for improvement of governance                         | ERAGS-MOD-CONF-001; ERAGS-MOD-CONF-002; ERAGS-MOD-CONF-003; ERAGS-MOD-KPI-003                                      | ERAGS-R-002; ERAGS-R-003; ERAGS-NF-002         |

## 4. Roles and Stakeholders

Roles referenced in these processes are aligned with:

- Stakeholder definitions in `ERAGS-DOC-STK-001`.
- Role usage in `ERAGS-MOD-PROC-001_Context_and_Stakeholder_Review_Model.md`.

Typical roles include (names indicative):

- Director – Roads Network Maintenance.
- Electrical Engineer – Roads Electrical Sub-Section (System 1 owner).
- Governance and Performance Analyst.
- HSE Representative.
- Configuration / Document Controller.
- CMMS / Data Integration Specialist.

Each SOP under `processes/` will include a **Roles and Responsibilities** section that references these roles explicitly.

## 5. Linkage to Requirements and RTM

For traceability:

- Every SOP should list the primary requirement IDs that it implements in its front matter (for example `ImplementsRequirements: [ERAGS-F-006, ERAGS-NF-006]`).
- `requirements/ERAGS_RTM.csv` will list each key SOP under `Implementing_Document_or_Process` for relevant requirements.

This ensures that:

- There is a clear path from requirement → model → process.
- Auditors can verify that each requirement has at least one implementing SOP where appropriate.

## 6. Maintenance of This Metadata File

When a new process is added or an existing one is retired:

1. Update this file to reflect:
   - New or changed Proc DocID.
   - File path.
   - Purpose and related models/requirements.
2. Ensure the SOP’s front matter and content are consistent with this index.
3. Update `ERAGS_RTM.csv` where necessary.

This keeps the process layer coherent and easy to navigate.
