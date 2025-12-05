---
DocID: ERAGS-MOD-FLOW-001
Title: ERAGS External Information Flows Model
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
  - ERAGS-MOD-ARCH-001
  - ERAGS-MOD-ARCH-002
  - ERAGS-MOD-DATA-001
  - ERAGS-MOD-DATA-002
  - ERAGS-REQ-IF-001
  - ERAGS-DOC-CTX-001
  - ERAGS-DOC-PROC-OV-001
RelatedFolders:
  - requirements/
  - models/03_data_models/
  - models/02_process_models/
  - qa/
---

# ERAGS External Information Flows Model

## 1. Purpose

This model describes the **external information flows** between ERAGS (System 1) and other subsystems or actors in the National Roads Electrical & Electronic Operations System (NRE²OS).

It supports and elaborates the interface requirements defined in ERAGS-REQ-IF-001, and clarifies how governance-level data entities (from `ERAGS-MOD-DATA-001` and `ERAGS-MOD-DATA-002`) are exchanged or consumed.

## 2. Scope

This document addresses:

- Information flows *into* ERAGS from external systems and stakeholders.
- Information flows *out of* ERAGS to external systems and stakeholders.
- Logical content and periodicity of these flows.

It does not describe internal ERAGS flows (those are covered in `ERAGS-MOD-FLOW-002_Internal_ERAGS_Information_Flows.md`) nor low-level technical protocols.

## 3. External Systems and Actors

External entities considered:

1. Roads Directorate Executive Management
2. Electrical Section Management and Supervisors
3. Human Resources and Competence Management System (System 2)
4. HSE and Incident Management System (System 3)
5. Asset Inventory and GIS System (System 4)
6. Maintenance and Operations Management (CMMS/WFM) System (System 5)
7. Street-Lighting Design and Energy Management System (System 6)
8. Traffic Signal Engineering and Operations System (System 7)
9. Security, Vandalism and Damage Management System (System 8)
10. Data, Analytics, KPI and Continuous Improvement System (System 9)
11. External Oversight and Audit Bodies

## 4. Summary of Key Flows

### 4.1 Inbound Flows (Into ERAGS)

| Flow ID | From System / Actor                                    | To ERAGS Component(s)                         | Content (Governance Entities)                                                               | Typical Frequency / Trigger            |
|--------|---------------------------------------------------------|-----------------------------------------------|---------------------------------------------------------------------------------------------|----------------------------------------|
| IF-IN-001 | CMMS/WFM (System 5)                                 | Data & Information Integration; KPI Mgmt      | PerformanceSummary, underlying fault and work statistics                                    | Monthly / Quarterly; on demand         |
| IF-IN-002 | Asset Inventory & GIS (System 4)                    | Data & Information Integration                | AssetGovernanceRecord subsets, location and administrative area mappings                    | Initial load; periodically (e.g. yearly) |
| IF-IN-003 | Finance / Energy Management (within Systems 5/6)    | Data & Information Integration; KPI Mgmt      | EnergyCostSummary, cost/budget allocations, tariff info                                     | Monthly / Quarterly                    |
| IF-IN-004 | HSE & Incident System (System 3)                    | Data & Information Integration; KPI Mgmt      | IncidentSummary, HSE alerts and incident classifications                                    | Monthly summary; immediate for serious incidents |
| IF-IN-005 | Security & Vandalism (System 8)                     | Data & Information Integration; Strategy Mgmt | IncidentSummary focused on vandalism/theft, hotspot indicators                              | Monthly / Quarterly; after major events |
| IF-IN-006 | Analytics / KPI System (System 9)                   | KPI Mgmt; Strategy Mgmt; Policy Mgmt          | KPIRecord sets, trend analyses, risk indicators                                            | Monthly / Quarterly; as requested      |
| IF-IN-007 | Electrical Section Management and Supervisors       | Policy Mgmt; Strategy Mgmt; Process Mgmt      | Qualitative feedback, feasibility constraints, emerging issues                              | As required; planning and review cycles |
| IF-IN-008 | Legal / Regulatory Sources (via advisors / context) | Policy Mgmt; Governance Process Mgmt          | Updates to laws, regulations, codes and standards (structured references and summaries)     | As published; periodic legal review    |
| IF-IN-009 | External Oversight and Audit Bodies                 | Governance Process Mgmt; Doc & Config Mgmt    | Audit findings, recommendations, compliance requirements                                   | Ad hoc (audit cycles)                  |

### 4.2 Outbound Flows (From ERAGS)

| Flow ID | From ERAGS Component(s)                          | To System / Actor                               | Content (Governance Entities)                                                               | Typical Frequency / Trigger              |
|--------|--------------------------------------------------|-------------------------------------------------|---------------------------------------------------------------------------------------------|------------------------------------------|
| IF-OUT-001 | Policy Mgmt; Doc & Config Mgmt              | All relevant subsystems and stakeholders        | Updated policies (GovernanceDocumentMetadata + full docs)                                  | After policy approval / revision        |
| IF-OUT-002 | Strategy Mgmt                               | Electrical Section Mgmt; CMMS/WFM; Exec Mgmt    | Asset Strategy updates, levels of service, strategic objectives                            | Strategy review cycle                    |
| IF-OUT-003 | Strategy Mgmt; Programme Governance         | CMMS/WFM; Finance                               | ProgrammeRecord lists (approved programmes and priorities)                                 | Annual / mid-cycle revisions             |
| IF-OUT-004 | KPI Mgmt; Analytics Interface               | Analytics / KPI System (System 9)               | KPI definition catalog (KPINamedID, formulas, targets, scope definitions)                  | When KPIs defined/changed; periodic sync |
| IF-OUT-005 | Requirements & Traceability Mgmt            | HR/Competence (System 2); HSE; CMMS/WFM         | Governance-level requirements on competence, safety, asset data and reporting              | On requirement changes; periodic review  |
| IF-OUT-006 | Governance Process Mgmt; Doc & Config Mgmt  | External Oversight and Audit Bodies             | DecisionLogEntry extracts, audit trail summaries, selected GovernanceDocumentMetadata      | On audit / oversight request             |
| IF-OUT-007 | Strategy Mgmt; KPI Mgmt                     | Roads Directorate Executive Management          | Summary performance reports, risk and opportunity analysis, recommended programmes         | Quarterly / annual performance cycle     |

## 5. Detailed Flow Descriptions

### 5.1 IF-IN-001: Performance Data from CMMS/WFM

- **Source:** Maintenance and Operations Management System (System 5).
- **Destination:** Data and Information Integration Component; Performance and KPI Management Component.
- **Content:**
  - Aggregated metrics in the form of PerformanceSummary records.
  - Underlying operational data (fault logs, work orders) as needed for drill-down.
- **Usage in ERAGS:**
  - Supports calculation of KPIs in KPIRecord.
  - Provides evidence for programme prioritisation and strategy reviews.
- **Related Requirements:**
  - ERAGS-D-002, ERAGS-F-006, ERAGS-F-008, ERAGS-IF-201.

### 5.2 IF-IN-002: Asset and Location Data from GIS

- **Source:** Asset Inventory and GIS System (System 4).
- **Destination:** Data and Information Integration Component.
- **Content:**
  - AssetGovernanceRecord subsets:
    - AssetClass, SubClass, LocationRef, Latitude/Longitude, AdministrativeArea, InstallYear, ConditionRating.
- **Usage in ERAGS:**
  - Determines where performance issues occur.
  - Links programmes to physical locations and asset populations.
- **Related Requirements:**
  - ERAGS-D-001, ERAGS-IF-101.

### 5.3 IF-IN-004: HSE Incident Data

- **Source:** HSE and Incident Management System (System 3).
- **Destination:** Data and Information Integration; KPI Management; Strategy Management.
- **Content:**
  - IncidentSummary records, grouped by area, corridor, or asset class.
- **Usage in ERAGS:**
  - Drives safety-related KPIs.
  - Influences policy and programme decisions (e.g. high-risk corridors).
- **Related Requirements:**
  - ERAGS-D-002, ERAGS-D-003, ERAGS-F-002, ERAGS-F-006.

### 5.4 IF-OUT-003: Programmes to CMMS/WFM and Finance

- **Source:** Strategy Management Component; Programme Governance.
- **Destination:** CMMS/WFM, Finance.
- **Content:**
  - ProgrammeRecord entries (scope, cost, timing, priority).
- **Usage in external systems:**
  - CMMS/WFM: create projects/work packages and schedule work.
  - Finance: allocate budgets and track expenditure.
- **Related Requirements:**
  - ERAGS-F-006, ERAGS-IF-301, ERAGS-D-002.

(Additional flows follow the same pattern inside the file; you already have the key pattern to extend if needed.)

## 6. Relationship to Data and Process Models

- This model uses entity definitions from:
  - `ERAGS-MOD-DATA-001_Governance_Data_Dictionary.md`
  - `ERAGS-MOD-DATA-002_Entity_Relationship_Model.md`

- It is consistent with:
  - Process models in `models/02_process_models/` (for example programme governance, policy management).
  - Architecture models in `models/01_architecture/` (which identify the components mentioned).

## 7. Traceability to Requirements

This model is an implementing artefact for:

- Data and interface requirements:
  - ERAGS-D-001, ERAGS-D-002, ERAGS-D-003.
  - ERAGS-IF-101..ERAGS-IF-502 (as defined in requirements).
- Functional requirements:
  - ERAGS-F-002, ERAGS-F-006, ERAGS-F-008.
- Non-functional requirements related to integration and traceability:
  - ERAGS-NF-002, ERAGS-NF-004.

These requirement IDs should reference this file in `ERAGS_RTM.csv` under `Implementing_Document_or_Process`.

## 8. Diagram Reference (Optional)

A graphical external flow diagram may be created and stored as:

- `models/04_information_flows/ERAGS-MOD-FLOW-001_External_Information_Flows.png`

and referenced from this document.
