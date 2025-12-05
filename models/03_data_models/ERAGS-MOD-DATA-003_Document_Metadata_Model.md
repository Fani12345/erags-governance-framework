---
DocID: ERAGS-MOD-DATA-003
Title: ERAGS Governance Document Metadata Model
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
  - ERAGS-REQ-HL-001
  - ERAGS-REQ-DATA-001
  - ERAGS-DOC-OV-000
RelatedFolders:
  - docs/
  - requirements/
  - models/06_configuration_and_metadata_models/
  - qa/
---

# ERAGS Governance Document Metadata Model

## 1. Purpose

This model describes how document metadata is structured and used across ERAGS governance artefacts in `/docs`, `/requirements`, `/models`, `/processes` and `/qa`. It implements ERAGS-D-004 (Document Metadata and Relationships) and supports documentation control and traceability requirements (ERAGS-F-009, ERAGS-R-003, ERAGS-NF-002, ERAGS-NF-003).

## 2. Metadata Fields

The governance document metadata is logically represented by the `GovernanceDocumentMetadata` entity in `ERAGS-MOD-DATA-001`. The standard fields are:

- DocID  
- Title  
- Version  
- Status  
- OwnerRole  
- OwnerName  
- ApproverRole  
- ApproverName  
- CreatedDate  
- LastUpdatedDate  
- System  
- RelatedDocs  
- RelatedFolders  

Each Markdown document in the ERAGS repository is expected to include these fields in its front-matter section.

## 3. Metadata Semantics

- **DocID** – Stable, unique identifier used for:
  - Traceability in the RTM.
  - Referencing in DecisionLogEntry.RelatedDocIDs.
  - Linking across models and processes.

- **Title** – Human-readable title that summarises the document’s purpose.

- **Version** – Indicates the current version:
  - Typical pattern: `0.1` for draft, `1.0` for first approved version.
  - Version changes are controlled by the Document and Configuration Management Component.

- **Status** – Lifecycle state of the document:
  - Draft, UnderReview, Approved, Superseded, Archived.
  - Status influences whether documents can be used as primary guidance in governance and operational processes.

- **OwnerRole / OwnerName** – Identify responsibility for content quality and updates.

- **ApproverRole / ApproverName** – Record governance approval, supporting auditability.

- **CreatedDate / LastUpdatedDate** – Support review cycles and trace recency.

- **System** – Identifies the system (e.g. ERAGS, future subsystems) to which the document belongs.

- **RelatedDocs** – Encodes key DocIDs that this document depends on or significantly influences.

- **RelatedFolders** – Encodes high-level folder dependencies (e.g. `docs/`, `requirements/`, `models/02_process_models/`).

## 4. Metadata Relationships

1. **To Requirements (RTM)**
   - DocID serves as the identifier used in `Implementing_Document_or_Process` column in `ERAGS_RTM.csv`.
   - Requirements refer to implementing documents by their DocID and path.
   - Changes to requirements may require updates to the metadata of implementing documents.

2. **To DecisionLogEntry**
   - DecisionLogEntry.RelatedDocIDs lists DocIDs of documents impacted by or supporting the decision.
   - This establishes an audit trail from decision to affected policies, strategies, models, etc.

3. **To Configuration and Baselines**
   - Baseline definitions reference sets of DocIDs and versions.
   - Configuration models in `models/06_configuration_and_metadata_models/` will treat each metadata instance as a configuration item.

## 5. Metadata Usage Rules

- All governance-relevant Markdown documents shall include the full metadata set.
- `DocID` values shall:
  - Be unique across ERAGS.
  - Follow a consistent naming pattern, e.g. `ERAGS-DOC-XXX-YYY`, `ERAGS-REQ-XXX-YYY`, `ERAGS-MOD-XXX-YYY`.

- `Status` changes from Draft to Approved should:
  - Be accompanied by a recorded decision in the decision log.
  - Involve updating LastUpdatedDate and, if appropriate, Version.

- `RelatedDocs` and `RelatedFolders` contributions shall:
  - Focus on the most important dependencies (not every minor reference).
  - Be maintained whenever new major relationships are introduced.

## 6. QA and Data Quality Implications

Metadata quality is critical to traceability. QA checks should include:

- Ensuring that all files in governance-related folders include mandatory metadata fields.
- Validating that DocID values are unique and non-empty.
- Checking that Referenced DocIDs in RelatedDocs and DecisionLogEntry exist as actual DocIDs.
- Monitoring completeness and correctness of CreatedDate and LastUpdatedDate.

These checks can be implemented as manual reviews or automated scripts and will be described in `/qa` artefacts.

## 7. Relationship to Other Models

- This metadata model is supported by:
  - `ERAGS-MOD-DATA-001` (data dictionary entry for GovernanceDocumentMetadata).
  - `ERAGS-MOD-CONF-001_Configuration_Item_And_Baseline_Model.md` (configuration item relationships).
  - `ERAGS-MOD-CONF-002_Governance_Document_Lifecycle_Model.md` (lifecycle states and transitions).

Together, they ensure that document metadata is not just a convention but a formalised part of the ERAGS data and configuration model.
