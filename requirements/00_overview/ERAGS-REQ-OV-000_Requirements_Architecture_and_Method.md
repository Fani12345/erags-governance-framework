---
DocID: ERAGS-REQ-OV-000
Title: ERAGS Requirements Architecture and Method
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
  - ERAGS-DOC-OV-000
  - ERAGS-DOC-CTX-001
  - ERAGS-DOC-STK-001
  - ERAGS-DOC-POL-001
  - ERAGS-DOC-STR-001
  - ERAGS-DOC-PROC-OV-001
  - ERAGS-DOC-REF-001
RelatedFolders:
  - docs/
  - models/
  - processes/
  - qa/
  - data/
---

# ERAGS Requirements Architecture and Method

## 1. Purpose

This document defines how requirements for the Electrical Roads Asset Governance & Strategy System (ERAGS) are structured, identified, maintained and traced. It ensures that requirements support the mission, policy and strategy defined in the `/docs` folder, and provide a robust basis for models, processes, data and quality-assurance activities.

## 2. Scope

The requirements covered by this architecture include:

- Governance and strategy for road-lighting, traffic-signal and associated electrical assets.
- Requirements on governance information, decision-making processes, performance monitoring and data.
- Interface requirements between ERAGS and other subsystems (for example CMMS/WFM, GIS, Finance, HSE and Analytics).

Operational-level requirements for field activities and subsystem-specific implementations are out of scope here, but will be derived later from ERAGS requirements.

## 3. Requirements Types and Identification

### 3.1 Types

ERAGS requirements are grouped into four main types:

- **Functional (F):** What ERAGS must do (policies, strategies, governance processes, KPIs).
- **Non-Functional (NF):** Quality attributes ERAGS must satisfy (availability, reliability, scalability, maintainability, performance, robustness, traceability, documentation control).
- **Data (D):** Requirements on the structure, quality, timeliness and metadata of governance-relevant data.
- **Regulatory/Compliance (R):** Requirements that ensure alignment with laws, regulations and standards.

### 3.2 Identification Scheme

Each requirement has a unique ID:

- `ERAGS-F-xxx` – Functional requirements.
- `ERAGS-NF-xxx` – Non-functional requirements.
- `ERAGS-D-xxx` – Data requirements.
- `ERAGS-R-xxx` – Regulatory/compliance requirements.

Where necessary, derived requirements may use suffixes, for example:

- `ERAGS-F-101-A` – Derived requirement from `ERAGS-F-101` for a specific component.

## 4. Folder Structure

Requirements are organised as follows:

- `01_high_level/` – High-level requirements for ERAGS as a governance and strategy system.
- `02_derived/` – Derived requirements for specific ERAGS components (policy library, strategy, governance processes, document control).
- `03_data_requirements/` – Detailed data and metadata requirements supporting ERAGS.
- `04_interface_requirements/` – Interface requirements between ERAGS and other subsystems or external systems.
- `05_change_history/` – Change log and baseline history for requirements.
- `06_baselines/` – Snapshots of requirement documents at key baselines.
- `ERAGS_RTM.csv` – Central Requirements Traceability Matrix linking all requirements to sources, implementations and verification.

## 5. Traceability and the RTM

Traceability is implemented via the file `requirements/ERAGS_RTM.csv`, which records, for each requirement:

- Requirement_ID  
- Requirement_Type  
- Source_Document (from `/docs`)  
- Implementing_Document_or_Process (from `/docs`, `/models`, `/processes`, `/qa`)  
- Data_Entities (from `/data` and `/models`)  
- Verification_Method (Review, Analysis, Inspection, Test)  
- Status (Planned, In Progress, Verified, etc.)

Bidirectional traceability means:

- For any requirement, it must be possible to trace **back** to:
  - Context, policy, strategy, stakeholders or regulatory drivers.
- For any governance artefact (document, model, process, QA test), it must be possible to trace **forward** to:
  - The requirement(s) it satisfies.

## 6. Relationship to Other ERAGS Artefacts

- `/docs` provides the narrative foundation from which high-level requirements are derived.
- `/requirements` captures those requirements formally and maintains their traceability.
- `/models` implements architecture and data models that are driven by these requirements.
- `/processes` describes governance workflows that satisfy specific requirements.
- `/qa` defines review and test activities that verify requirements.
- `/data` contains example or reference datasets and schemas that demonstrate compliance with data requirements.

## 7. Change Control for Requirements

Changes to requirements shall follow this process:

1. **Change Proposal:** Any change to an existing requirement or creation of a new requirement is proposed and logged in `requirements/05_change_history/ERAGS-REQ-CH-LOG.md`.
2. **Impact Assessment:** The impact of the change on documents, models, processes, data and QA plans is analysed.
3. **Approval:** Changes are approved through the ERAGS governance process defined in ERAGS-DOC-PROC-OV-001.
4. **Implementation:** Requirements and related artefacts are updated, and the RTM is revised accordingly.
5. **Baseline Update:** For major changes, a new baseline is recorded in `06_baselines/` and may be associated with a Git tag.

## 8. Quality Attributes for the Requirements System

The requirements system itself shall satisfy:

- **Clarity:** Requirements are unambiguous, concise and written as “shall” statements.
- **Consistency:** Requirements do not contradict each other or underlying policy/strategy.
- **Completeness:** Requirements cover key aspects of governance, strategy, data and interfaces for ERAGS.
- **Traceability:** As described, every requirement has clear sources and implementations.
- **Verifiability:** Each requirement has a defined verification method that can be practically applied.
- **Maintainability:** The folder structure, identification scheme and RTM support efficient updates and reviews.

These attributes are enforced via QA plans in the `/qa` folder and periodic requirement reviews.
