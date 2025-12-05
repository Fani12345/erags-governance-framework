---
DocID: ERAGS-MOD-OV-000
Title: ERAGS Models Architecture and Method
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
  - ERAGS-DOC-CTX-001
  - ERAGS-DOC-STK-001
  - ERAGS-DOC-POL-001
  - ERAGS-DOC-STR-001
  - ERAGS-DOC-PROC-OV-001
  - ERAGS-REQ-OV-000
  - ERAGS-REQ-HL-001
RelatedFolders:
  - docs/
  - requirements/
  - processes/
  - qa/
  - data/
---

# ERAGS Models Architecture and Method

## 1. Purpose

This document defines how models for the Electrical Roads Asset Governance & Strategy System (ERAGS) are organised and used. It explains:

- What model types exist in the `models/` folder.
- How models relate to documents in `docs/` and requirements in `requirements/`.
- How model identifiers are assigned and referenced.
- How models support processes and quality assurance.

The objective is to ensure that all models form a coherent, traceable representation of System 1 – ERAGS inside the wider National Roads Electrical & Electronic Operations System (NRE²OS).

## 2. Scope

The modelling scope covers:

- ERAGS as a system-of-interest (System 1), including its internal components and external interfaces.
- Governance-level information flows and data structures (not low-level CMMS or SCADA schemas).
- KPI and decision logic models used by governance processes.
- Configuration and metadata models for documentation and baselines.

Operational and hardware-level models of field equipment (luminaires, controllers, networks) are out of scope here and belong to other subsystems.

## 3. Model Types and Naming

### 3.1 Model Types

The following model types are used:

- **Architecture Models (ARCH):**
  - System context view.
  - Internal logical architecture.
  - Component responsibilities.

- **Process Models (PROC):**
  - Governance process flows (for example context review, policy management, programme governance).

- **Data Models (DATA):**
  - Governance data dictionary.
  - Entity-relationship structures for governance data.
  - Document metadata structures.

- **Information Flow Models (FLOW):**
  - External flows between ERAGS and other subsystems (CMMS/WFM, GIS, Finance, HSE, Analytics).
  - Internal flows between ERAGS components.

- **KPI and Analytics Models (KPI):**
  - KPI definitions and calculation logic.
  - Governance decision rules based on KPI thresholds and trends.

- **Configuration and Metadata Models (CONF):**
  - Configuration items and baselines.
  - Governance document lifecycle and states.

### 3.2 Model Identification Scheme

Models are identified using the pattern:

- `ERAGS-MOD-<TYPE>-NNN_<Descriptive_Name>.md`

where:

- `<TYPE>` ∈ {`ARCH`, `PROC`, `DATA`, `FLOW`, `KPI`, `CONF`}
- `NNN` is a three-digit sequence number.
- `<Descriptive_Name>` is a concise, descriptive title using underscores.

Example:

- `ERAGS-MOD-ARCH-001_System_Context_Diagram.md`
- `ERAGS-MOD-DATA-001_Governance_Data_Dictionary.md`

Where appropriate, separate image files (for example PNG diagrams) may be referenced from within the Markdown model documents.

## 4. Folder Structure

Models are organised as follows:

- `01_architecture/`
  - System context, logical architecture and component responsibilities.
- `02_process_models/`
  - Models for key governance processes.
- `03_data_models/`
  - Governance data dictionary and entity relations.
- `04_information_flows/`
  - External and internal information flows.
- `05_kpi_and_analytics_models/`
  - KPI definitions and governance decision logic.
- `06_configuration_and_metadata_models/`
  - Configuration items, baselines and document lifecycle models.

This folder-level structuring supports modularity and maintainability (ERAGS-NF-003 and ERAGS-NF-004).

## 5. Relationship to Requirements, Documents and Processes

### 5.1 Relationship to Requirements

Each model document shall:

- Reference the relevant requirement IDs from `ERAGS-REQ-HL-001` and any derived requirements.
- Be listed in `requirements/ERAGS_RTM.csv` under `Implementing_Document_or_Process` for those requirements.

The intention is that:

- High-level requirements describe *what* ERAGS must do.
- Models describe *how* those requirements are structurally organised.

### 5.2 Relationship to Documents in `docs/`

Architecture and context models in `models/01_architecture/` are grounded in:

- Context and mission (ERAGS-DOC-CTX-001).
- Stakeholder roles (ERAGS-DOC-STK-001).
- Policy and strategy (ERAGS-DOC-POL-001 and ERAGS-DOC-STR-001).
- Governance process overview (ERAGS-DOC-PROC-OV-001).

These documents provide narrative descriptions; models provide structured views that can be more easily analysed and tested.

### 5.3 Relationship to Process Descriptions in `processes/`

Process models in `models/02_process_models/`:

- Provide formal views (flows, states) for the processes described textually in `/processes`.
- Help ensure that all steps, roles and decision points are clearly identified and linked to requirements.

### 5.4 Relationship to QA Artefacts in `qa/`

KPI, data, flow and configuration models support QA by:

- Providing reference definitions for what “correct” looks like.
- Enabling QA scripts and checklists to validate:
  - Data completeness and consistency.
  - Traceability and configuration of governance artefacts.
  - Correct triggering of governance processes from KPI thresholds or incidents.

## 6. Modelling Conventions

- Models are primarily maintained as Markdown (`.md`), with diagrams embedded as images where necessary.
- Each model document includes:
  - Metadata header consistent with other ERAGS documents.
  - Clear statement of purpose and scope.
  - Traceability to specific requirement IDs.
  - Explanations of how the model should be interpreted.

Where diagrams are used:

- The diagram file names will follow the same ID pattern, for example:
  - `ERAGS-MOD-ARCH-001_System_Context_Diagram.png`
- Markdown files will embed or reference the diagram.

## 7. Change Control for Models

Changes to models follow the broader ERAGS change-control approach:

1. A change is proposed (triggered by requirement change, new insight or correction).
2. The impact on requirements, processes and QA artefacts is assessed.
3. The change is approved through the governance processes defined in ERAGS-DOC-PROC-OV-001.
4. The model is updated, and the RTM and change log are adjusted accordingly.
5. For significant changes, a new baseline may be established and tagged in Git.

This ensures that models remain synchronised with requirements, documents and implemented processes.
