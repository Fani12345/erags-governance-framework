---
DocID: ERAGS-PROC-006
Title: Document Lifecycle and Baseline Management SOP
Version: 0.1
Status: Draft
OwnerRole: Electrical Engineer – Roads Electrical Sub-Section (System 1 Owner)
OwnerName: Fani Masoabi
ApproverRole: Director – Roads Network Maintenance
ApproverName: (to be designated)
CreatedDate: 2025-12-05
LastUpdatedDate: 2025-12-05
System: ERAGS (Electrical Roads Asset Governance & Strategy System)
ProcessFamily: ChangeAndConfiguration
RelatedModels:
  - ERAGS-MOD-CONF-001
  - ERAGS-MOD-CONF-002
  - ERAGS-MOD-CONF-003
  - ERAGS-MOD-DATA-001
  - ERAGS-MOD-DATA-003
  - ERAGS-MOD-ARCH-001
  - ERAGS-MOD-ARCH-002
  - ERAGS-MOD-ARCH-003
RelatedDocs:
  - ERAGS-DOC-CTX-001
  - ERAGS-DOC-POL-001
  - ERAGS-DOC-STR-001
  - ERAGS-DOC-OV-000
  - ERAGS-DOC-PROC-OV-001
  - ERAGS-DOC-STK-001
RelatedDataEntities:
  - GovernanceDocumentMetadata
  - ConfigurationItem
  - BaselineRecord
  - DecisionLogEntry
ImplementsRequirements:
  - ERAGS-F-009
  - ERAGS-D-004
  - ERAGS-NF-001
  - ERAGS-NF-002
  - ERAGS-NF-003
  - ERAGS-R-003
---

# Document Lifecycle and Baseline Management SOP  
*(ERAGS-PROC-006)*

## 1. Purpose

This Standard Operating Procedure defines how System 1 – ERAGS manages the:

- **Lifecycle of governance documents** (from Draft to Archived).
- **Baselines** that capture stable reference states of the governance configuration.

The process ensures that:

- Each governance document has clear status, version and ownership.
- Changes to documents are controlled and traceable.
- Baselines provide auditable “snapshots” of System 1 at key points in time (for example before a major programme, or at the time of a submission).

## 2. Scope

This SOP applies to all governance documents for System 1, including but not limited to:

- Context, policy, strategy and overview documents in `docs/`.
- Requirements and RTM in `requirements/`.
- Models in `models/` (architecture, process, data, KPI, configuration, etc.).
- Process SOPs in `processes/`.
- QA plans and checklists in `qa/` when they form part of the governance configuration.

It covers:

- Lifecycle states as defined in `ERAGS-MOD-CONF-002_Governance_Document_Lifecycle_Model.md`.
- Baseline creation, update and closure as defined in `ERAGS-MOD-CONF-001_Configuration_Item_And_Baseline_Model.md`.
- Repository metadata and Git workflow alignment as defined in `ERAGS-MOD-CONF-003_Repository_Metadata_and_Git_Workflow_Model.md`.

## 3. Lifecycle States

Lifecycle states are defined in detail in `ERAGS-MOD-CONF-002`, but for the purposes of this SOP the main states are:

- **Draft**
  - Content under development, not yet ready for formal review.
- **UnderReview**
  - Content stable enough for structured review.
- **Approved**
  - Content authorised for use as current reference.
- **Superseded**
  - Content replaced by a newer Approved version.
- **Archived**
  - Content no longer active; retained only for historical or audit reasons.

All lifecycle state changes are recorded in **GovernanceDocumentMetadata** and, where relevant, are linked to Change Control (ERAGS-PROC-005).

## 4. Baseline Concepts

A **baseline** is a named, controlled snapshot of a coherent set of System 1 configuration items (documents, models, processes, etc.) at a particular point in time.

- Baselines are represented as **BaselineRecord** entities.
- Each BaselineRecord:
  - Has a unique BaselineID and name.
  - Specifies its scope (which CIs it includes).
  - References the Git tag or commit representing that state.
  - Has a purpose (for example “System 1 – Initial Governance Baseline”).

Baselines are used to:

- Provide stable references for submissions, audits, programme approvals, etc.
- Allow comparison of governance configuration over time.

## 5. Roles and Responsibilities

- **Electrical Engineer – Roads Electrical Sub-Section (System 1 Owner)**
  - Owns the document lifecycle and baseline management process.
  - Decides when baselines should be created or updated.
  - Ensures that lifecycle changes remain consistent with governance needs.

- **Configuration / Document Controller**
  - Maintains GovernanceDocumentMetadata for all documents in scope.
  - Maintains the CI register and BaselineRecord entries.
  - Applies lifecycle changes and coordinates baseline creation and updates.
  - Ensures alignment with Git workflow and repository conventions.

- **Document/Model Authors**
  - Develop and revise documents and models within this lifecycle framework.
  - Ensure correctness and completeness of content.

- **ChangeReviewGroup (CRG) and Approval Authorities**
  - Provide approvals via the Change Control process where lifecycle changes are connected to significant governance changes.

## 6. Inputs

1. **GovernanceDocumentMetadata**
   - Current records of documents, their lifecycle states and versions.

2. **CI register**
   - List of configuration items and the documents/models associated with them.

3. **BaselineRecord set**
   - Current baselines and their scopes.

4. **ChangeRequests and DecisionLogEntry**
   - Triggers for lifecycle changes or baseline creation.

5. **Repository and Git state**
   - Current branches, commits and tags as per `ERAGS-MOD-CONF-003`.

## 7. Pre-Conditions

Before changing document lifecycle states or baselines:

1. The System 1 Owner must:
   - Confirm the reason for the change (for example approval of a new version, retirement of an obsolete document, creation of a baseline for a submission).

2. The Configuration / Document Controller must:
   - Confirm the current lifecycle state and version of the document(s).
   - Check whether the change requires Change Control (ERAGS-PROC-005).
   - Ensure that the repository branch/commit structure supports the intended baseline or lifecycle update.

## 8. Procedure – Document Lifecycle Management

### 8.1 Step 1 – Create New Document (Draft)

When a new governance document is created:

1. The Author creates the file in the appropriate folder (for example `docs/`, `models/`, `processes/`, `qa/`).
2. The Author includes:
   - A unique DocID in the YAML front matter.
   - Initial metadata:
     - Title.
     - Version = 0.1.
     - Status = Draft.
     - OwnerRole and OwnerName.
     - RelatedModels, RelatedDocs, RelatedFolders as applicable.
3. The Configuration / Document Controller:
   - Registers the document as a ConfigurationItem in the CI register.
   - Ensures that the DocID and file path are unique and consistent with naming conventions.

### 8.2 Step 2 – Progress Draft to UnderReview

When the Author considers the Draft to be ready for review:

1. The Author notifies the System 1 Owner and Configuration / Document Controller.
2. If the change is minor (for example small clarifications), the System 1 Owner may allow direct progression; if the change is major, a ChangeRequest should be raised.
3. The Configuration / Document Controller updates the GovernanceDocumentMetadata:
   - Status = UnderReview.
   - Version remains as is or is incremented if required by the local convention (for example from 0.1 to 0.2).
   - LastUpdatedDate set to the date of promotion.

### 8.3 Step 3 – Approval and Status Change to Approved

Once review is complete and approval is granted (via the appropriate process, typically ERAGS-PROC-005 for significant items):

1. The Approval Authority’s decision is recorded as a DecisionLogEntry.
2. The Configuration / Document Controller updates document metadata:
   - Status = Approved.
   - Version:
     - For a new document: set to 1.0.
     - For a major revision: increment major version (for example 1.0 → 2.0).
     - For a minor revision: increment minor version (for example 1.0 → 1.1) as per local rules.
   - EffectiveDate (if used) is set.
   - Supersedes and SupersededBy fields are updated for relevant documents.

3. If the document is part of a defined baseline scope and the approval represents a significant configuration milestone, this may trigger creation or update of a BaselineRecord (see Section 9).

### 8.4 Step 4 – Superseding and Archiving Documents

When new versions are Approved:

1. The previous Approved version is:
   - Marked Status = Superseded in metadata.
   - Linked via SupersededBy to the new version.

2. When a document is no longer needed, even as a superseded reference, the System 1 Owner may decide to **Archive** it:

   - Status = Archived.
   - ArchiveDate set in metadata.

3. Archived documents:

   - Are retained for historical and audit purposes.
   - Are clearly labelled to prevent accidental use as current references.

## 9. Procedure – Baseline Management

### 9.1 Step 1 – Decide to Create or Update a Baseline

Baselines are created or updated when:

- A major governance configuration state is reached (for example “System 1 – Initial ERAGS Baseline”).
- A submission or audit requires an explicit reference configuration.
- A significant programme or policy decision depends on a stable configuration snapshot.

The System 1 Owner proposes the baseline and its scope; the decision to create/update a baseline may itself be recorded as a DecisionLogEntry.

### 9.2 Step 2 – Define Baseline Scope

For a new or updated baseline:

1. The System 1 Owner and Configuration / Document Controller define:

   - BaselineID and name.
   - Purpose (for example “Baseline for Roads Electrical Engineer application portfolio – System 1”).
   - List or rule-based description of included ConfigurationItems:
     - For example: “All Approved documents in `docs/`, `requirements/`, `models/`, `processes/` as of 2025-12-10.”

2. This is recorded as a preliminary **BaselineDefinition** in the BaselineRecord.

### 9.3 Step 3 – Align Repository State (Git)

1. The Configuration / Document Controller ensures that:

   - All relevant content is committed to the repository.
   - The main or baseline branch reflects the intended configuration state.

2. A specific Git commit is identified as the baseline anchor.

3. A Git **tag** is created according to the conventions in `ERAGS-MOD-CONF-003`, for example:

   - `baseline/ERAGS-SYS1-INITIAL-001`
   - `baseline/ERAGS-SYS1-PORTFOLIO-2025-12`

### 9.4 Step 4 – Finalise BaselineRecord

The BaselineRecord is updated to include:

- BaselineID and name.
- Purpose and description.
- Scope (ConfigurationItems or inclusion rules).
- Git tag or commit hash.
- CreatedDate.
- OwnerRole and OwnerName.
- Related DecisionLogEntry (if any).

Status of the baseline (for example Active, Closed) is also recorded.

### 9.5 Step 5 – Use and Maintain Baseline

1. When a baseline is **Active**:

   - It may form the reference for:
     - Reports and submissions.
     - Demonstrations of governance configuration (for example to a reviewer).

2. Over time the System 1 configuration may evolve beyond this baseline:

   - The baseline remains a reference snapshot.
   - New baselines may be created when needed.

3. When a baseline is no longer needed as an active reference but must be retained for history or audit:

   - Status may be set to Closed.
   - It remains associated with its Git tag, which is not reused.

## 10. Interaction with Change Control

- Document lifecycle changes and baseline definitions are often interconnected with the Change Control process (ERAGS-PROC-005).

- For significant governance changes:

  - A ChangeRequest should be raised.
  - The ChangeRequest and DecisionLogEntry should reference which documents and baselines are affected.
  - Implementation of changes should follow ERAGS-PROC-005, after which this SOP is used to update lifecycle states and baselines.

## 11. Outputs and Records

Key outputs of this SOP include:

1. **Updated GovernanceDocumentMetadata**
   - Reflecting correct lifecycle state, version, relationships and dates.

2. **ConfigurationItem (CI) records**
   - Updated with lifecycle state and baseline membership.

3. **BaselineRecord entries**
   - Capturing defined baselines, scopes, Git tags and purposes.

4. **DecisionLogEntry**
   - When baselines are created or lifecycle changes are associated with governance decisions.

These records ensure full traceability and auditability of document and baseline states.

## 12. Metrics and Effectiveness Checks

Effectiveness of this SOP can be evaluated via:

1. **Metadata completeness**
   - Percentage of governance documents with complete and consistent metadata (DocID, Status, Version, Owner, etc.).

2. **Lifecycle accuracy**
   - Number of discrepancies found between actual document use and recorded lifecycle state.

3. **Baseline usage**
   - Evidence that key submissions and reviews reference a specific BaselineRecord and Git tag.

4. **Audit findings**
   - Frequency and severity of audit issues related to documentation control and baselines.

These checks can later be encoded as QA checks under `/qa`.

## 13. Compliance and Audit Considerations

Auditors should be able to:

- Select a document and see:

  - Its lifecycle history (Draft → UnderReview → Approved → Superseded/Archived).
  - Associated CIs and baselines.
  - Related change and decision records.

- Select a baseline and see:

  - The set of documents and models included.
  - The corresponding Git tag/commit.
  - The purpose and context for which the baseline was created.

- Confirm that:

  - No major governance artefacts are used operationally while remaining in Draft or UnderReview without appropriate controls.
  - Document and baseline management align with the configuration models and Change Control SOP.

This completes the definition of ERAGS-PROC-006 Document Lifecycle and Baseline Management SOP.
