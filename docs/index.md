---
DocID: ERAGS-DOC-OV-000
Title: ERAGS Document Map and Relationships
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
  - ERAGS-DOC-CTX-001
  - ERAGS-DOC-STK-001
  - ERAGS-DOC-POL-001
  - ERAGS-DOC-STR-001
  - ERAGS-DOC-PROC-OV-001
  - ERAGS-DOC-REF-001
RelatedFolders:
  - requirements/
  - models/
  - processes/
  - qa/
  - data/
---

# ERAGS Document Map and Relationships

This document provides an overview of all documentation within the Electrical Roads Asset Governance & Strategy System (ERAGS) and how each document relates to other artefacts and folders in the repository.

## 1. Document Inventory

| DocID                     | Title                                                 | Folder                | Primary Purpose                              | Key Relationships                                                 |
|---------------------------|-------------------------------------------------------|-----------------------|----------------------------------------------|-------------------------------------------------------------------|
| ERAGS-DOC-CTX-001        | Context and Mission                                   | 01_context/           | Define mission, scope and external drivers   | Feeds: ERAGS-DOC-POL-001, ERAGS-DOC-STR-001                      |
| ERAGS-DOC-STK-001        | Stakeholders and Roles                                | 02_stakeholders/      | Identify stakeholders and responsibilities   | Feeds: governance processes, requirements in /requirements        |
| ERAGS-DOC-POL-001        | Asset Management Policy                               | 03_policies/          | High-level asset management direction        | Based on: CTX-001; Drives: STR-001, PROC-OV-001                   |
| ERAGS-DOC-STR-001        | Lighting and Signals Asset Strategy                   | 04_strategies/        | Long-term lifecycle approach                 | Implements: POL-001; Feeds: requirements, models, processes       |
| ERAGS-DOC-PROC-OV-001    | Governance Process Overview                           | 05_process_overview/  | Defines ERAGS governance workflows           | Implements: POL-001; Linked to /processes, /models                |
| ERAGS-DOC-REF-001        | Glossary and Abbreviations                            | 06_glossary/          | Define terms used across ERAGS               | Referenced by all other documents                                 |

## 2. Logical Relationships Between Documents

- **ERAGS-DOC-CTX-001 (Context and Mission)**  
  - Provides the external and internal context for ERAGS.  
  - Its content justifies and constrains the Asset Management Policy (ERAGS-DOC-POL-001).

- **ERAGS-DOC-STK-001 (Stakeholders and Roles)**  
  - Defines who is Responsible, Accountable, Consulted and Informed (RACI) for ERAGS decisions.  
  - Used by all process descriptions to assign roles.

- **ERAGS-DOC-POL-001 (Asset Management Policy)**  
  - Sets principles for how road-lighting and traffic-signal assets are governed.  
  - Directly drives the Asset Strategy (ERAGS-DOC-STR-001) and Governance Processes (ERAGS-DOC-PROC-OV-001).  

- **ERAGS-DOC-STR-001 (Lighting and Signals Asset Strategy)**  
  - Interprets the policy into lifecycle strategies and high-level programmes.  
  - Feeds into requirements in `/requirements` and models in `/models`.

- **ERAGS-DOC-PROC-OV-001 (Governance Process Overview)**  
  - Describes the main ERAGS governance workflows (policy review, strategy updates, change control).  
  - Each process is documented in more detail in `/processes`.

- **ERAGS-DOC-REF-001 (Glossary and Abbreviations)**  
  - Standardises terms across all documents.  
  - All other documents should avoid defining conflicting terms.

## 3. Relationships to Other Folders

- **/requirements**  
  - Contains the ERAGS high-level requirements and RTM.  
  - Requirements explicitly refer to documents defined in this index.

- **/models**  
  - Holds architecture diagrams and data models that are justified by CTX-001, POL-001 and STR-001.

- **/processes**  
  - Contains detailed process descriptions aligned with PROC-OV-001 and STK-001.

- **/qa**  
  - Contains QA plans and test scenarios referencing requirements and specific documents.

- **/data**  
  - Stores example or reference data structures described in STR-001 and models.

## 4. Change Management

Any new document added to ERAGS shall:
- Be assigned a unique DocID.
- Be listed in the table in Section 1 of this index.
- Include a metadata block consistent with this document.
- Be linked to relevant requirements and processes through updates to the RTM in `/requirements`.
