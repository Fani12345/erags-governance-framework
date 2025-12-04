---
DocID: ERAGS-REQ-DER-000
Title: Index of Derived Requirements for ERAGS Components
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
  - models/
  - processes/
  - qa/
---

# Index of Derived Requirements for ERAGS Components

## 1. Purpose

This document provides an index and overview of derived requirements for specific ERAGS components. It links high-level requirements to more detailed, component-level requirements, which then drive models, processes and QA activities.

## 2. Derived Requirements Documents

The following component-level derived requirement documents will be maintained in this folder:

- `ERAGS-REQ-DER-001_Policy_and_Strategy_Component_Requirements.md`  
  - Derived requirements for the policy and strategy components (Policy Library and Asset Strategy).
- `ERAGS-REQ-DER-002_Governance_Process_Component_Requirements.md`  
  - Derived requirements for governance process components (context review, policy review, strategy review, programme governance, change control).
- `ERAGS-REQ-DER-003_Document_and_Configuration_Management_Requirements.md`  
  - Derived requirements for document metadata, version control and configuration management in support of ERAGS.

Each of these documents will:

- Reference the high-level requirement IDs from ERAGS-REQ-HL-001 (for example ERAGS-F-001, ERAGS-NF-003, ERAGS-D-004).
- Specify more detailed, testable requirements for specific components or functions.
- Provide clear input to models in `/models`, process descriptions in `/processes` and QA checks in `/qa`.

## 3. Relationship to High-Level Requirements

Derived requirements:

- Must **not** introduce new objectives that contradict high-level requirements.
- Must remain traceable by referencing relevant high-level requirement IDs.
- Must be listed in the `ERAGS_RTM.csv` file with links to their implementing artefacts.

Future updates to high-level requirements require a review of all derived requirements to confirm ongoing alignment.

## 4. Relationship to Other Folders

- `/models` uses derived requirements to create architecture and data models for individual components.
- `/processes` uses derived requirements to design and document detailed workflows.
- `/qa` defines tests and reviews that verify compliance with derived requirements.
