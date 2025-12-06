---
DocID: ERAGS-PROC-005
Title: Change Control SOP
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
  - ERAGS-MOD-ARCH-001
  - ERAGS-MOD-ARCH-002
  - ERAGS-MOD-ARCH-003
  - ERAGS-MOD-DATA-001
  - ERAGS-MOD-DATA-003
  - ERAGS-MOD-FLOW-002
RelatedDocs:
  - ERAGS-DOC-CTX-001
  - ERAGS-DOC-POL-001
  - ERAGS-DOC-STR-001
  - ERAGS-DOC-PROC-OV-001
  - ERAGS-DOC-STK-001
RelatedDataEntities:
  - ConfigurationItem
  - GovernanceDocumentMetadata
  - BaselineRecord
  - DecisionLogEntry
  - ChangeRequest
  - KPIRecord
ImplementsRequirements:
  - ERAGS-F-007
  - ERAGS-F-009
  - ERAGS-D-004
  - ERAGS-NF-001
  - ERAGS-NF-002
  - ERAGS-NF-003
  - ERAGS-R-003
Alias:
  - PROC-Change-Control
---

# Change Control SOP  
*(ERAGS-PROC-005 / “PROC-Change-Control”)*

## 1. Purpose

This Standard Operating Procedure defines the **Change Control process** for System 1 – ERAGS governance artefacts, including:

- Policies, strategies and governance processes.
- Requirements and models.
- KPI definitions and thresholds.
- Key configuration and metadata conventions.

The process ensures that changes:

- Are initiated for justified reasons.
- Undergo impact analysis and structured review.
- Are approved by the appropriate authority.
- Are implemented in a controlled, traceable manner.
- Are captured in configuration items (CIs), baselines and metadata.

## 2. Scope

This SOP applies to **governance-level configuration items** within System 1 – ERAGS, as defined in:

- `ERAGS-MOD-CONF-001_Configuration_Item_And_Baseline_Model.md`
- `ERAGS-MOD-CONF-002_Governance_Document_Lifecycle_Model.md`
- `ERAGS-MOD-CONF-003_Repository_Metadata_and_Git_Workflow_Model.md`

Examples of items under this change control include:

- Governance documents:
  - Context, policy and strategy documents.
  - Process overviews and SOPs under `processes/`.
- Requirements artefacts:
  - `requirements/*` including the RTM.
- Models:
  - Architecture, process, data, information flow, KPI, configuration models under `models/`.
- Metadata conventions and configuration rules:
  - Document naming, DocID schemes, lifecycle rules, Git practices.

Out of scope:

- Low-level operational changes in external systems (CMMS, WFM, GIS, etc.), which follow their own change processes.
- Detailed design changes in field hardware or software solutions (unless specifically elevated as governance CIs).

## 3. Triggers

Change Control is triggered by:

1. **Governance decisions**
   - From Strategy and Governance Review (ERAGS-PROC-001).
   - From Programme Governance (ERAGS-PROC-002).
   - From Performance and KPI Review (ERAGS-PROC-003).
   - From Policy Management (ERAGS-PROC-004).
   - From Incident-driven interventions (ERAGS-PROC-008).

2. **Configuration management findings**
   - Inconsistencies or gaps identified in governance artefacts or metadata.
   - Misalignments between repository content and documented conventions.

3. **External changes**
   - New legal, regulatory or organisational requirements that require CI updates.

4. **Quality and audit findings**
   - Audit observations indicating that documentation or models must be corrected or updated.

Each proposed change is captured as a **ChangeRequest**.

## 4. Roles and Responsibilities

(Aligned with ERAGS-DOC-STK-001 and configuration models.)

- **Electrical Engineer – Roads Electrical Sub-Section (System 1 Owner)**
  - Process owner for Change Control.
  - Ensures that changes are aligned with governance objectives.
  - Chairs or coordinates the change review where required.

- **Configuration / Document Controller**
  - Maintains the CI register and BaselineRecord entries.
  - Ensures that each change is correctly recorded and linked to artefacts.
  - Oversees metadata updates and Git workflow adherence.

- **Change Originator**
  - Any authorised stakeholder who identifies the need for change.
  - Raises the ChangeRequest with sufficient detail and justification.

- **Change Review Group (CRG)**
  - Composition may vary depending on the change; typically includes:
    - System 1 Owner.
    - Governance and Performance Analyst.
    - Legal/Regulatory Representative (if relevant).
    - Technical Standards/Engineering Representative (if relevant).
    - HSE Representative (for safety-related content).
  - Reviews impact and recommends approval or rejection.

- **Approval Authority**
  - Typically the Director – Roads Network Maintenance for major governance changes.
  - May be delegated for minor changes as defined in local policy.

## 5. Inputs

1. **ChangeRequest**
   - Description of the proposed change.
   - Reason/justification.
   - Affected CIs (documents, models, metadata rules).
   - Originating decision, incident, audit finding or other trigger.

2. **Current CI register and BaselineRecord**
   - List of existing configuration items and baselines.
   - Lifecycle status and version of affected items.

3. **Related governance artefacts**
   - Policies, strategies, requirements, models, processes, metadata conventions.

4. **Supporting evidence**
   - KPI and performance data.
   - Incident information.
   - Audit findings.
   - Regulatory or standards references.

## 6. Pre-Conditions

Before a ChangeRequest proceeds to formal review:

1. The ChangeRequest must be **properly logged** with:
   - Unique ChangeRequest ID.
   - Clear description and justification.
   - Identification of affected CIs (as far as known).

2. The Configuration / Document Controller must:
   - Confirm that the listed CIs exist in the CI register.
   - Retrieve current version, status and related baselines.

3. For major changes, the System 1 Owner must:
   - Confirm that the change is consistent with current governance context and priorities.
   - If necessary, link the ChangeRequest to a specific DecisionLogEntry.

## 7. Procedure

### 7.1 Step 1 – Raise ChangeRequest

1. The Change Originator completes a **ChangeRequest** entry containing at minimum:
   - ChangeRequest ID.
   - Title and short description.
   - Trigger and justification.
   - Affected CIs (if known).
   - Proposed priority (for example Low, Medium, High).
   - Proposed change type:
     - Correction (for example fixing errors).
     - Enhancement (for example improving clarity or structure).
     - New item.
     - Retirement/deprecation.

2. The ChangeRequest is submitted to the System 1 Owner and Configuration / Document Controller.

### 7.2 Step 2 – Initial Screening

1. The Configuration / Document Controller:
   - Verifies CI references and fills in missing CI details where possible.
   - Checks for duplicate or overlapping ChangeRequests.

2. The System 1 Owner:
   - Screens the request for:
     - Obvious misalignment with governance direction.
     - Trivial issues that can be handled via clearly defined minor-change paths if such exist.

3. Outcome of screening:
   - **Accept for review** (most cases).
   - **Reject** (if clearly invalid or redundant), with rationale recorded.
   - **Defer** (if dependent on other decisions or conditions).

### 7.3 Step 3 – Impact Analysis

For ChangeRequests accepted for review:

1. The System 1 Owner, with support from relevant roles, performs an **impact analysis** that covers:

   - Affected CIs:
     - Which documents, models, requirements, metadata rules are impacted.
   - Traceability effects:
     - Links in the RTM, models and processes that may be affected.
   - Consistency with baselines:
     - Which BaselineRecord(s) will be affected or need adjustment.
   - Potential impacts on:
     - KPIs and reporting.
     - Programmes and policies.
     - External interfaces and stakeholders.

2. The analysis is captured in a **Change Impact Note**, linked to the ChangeRequest.

### 7.4 Step 4 – Change Review (CRG)

1. The ChangeReviewGroup (CRG) convenes or reviews the ChangeRequest and Impact Note asynchronously, depending on complexity.

2. The CRG assesses:

   - Adequacy of justification.
   - Completeness of Impact Note.
   - Risks of making the change vs leaving the configuration as-is.
   - Any sequencing or dependencies between this and other changes.

3. The CRG recommends one of:

   - **Approve as proposed**.
   - **Approve with conditions** (for example additional checks or staged application).
   - **Request further analysis or revisions to the change proposal**.
   - **Reject**.

4. The recommendation, rationale and any conditions are recorded against the ChangeRequest.

### 7.5 Step 5 – Approval Decision

1. The appropriate Approval Authority (for example Director – Roads Network Maintenance for major changes):

   - Reviews the ChangeRequest, Impact Note and CRG recommendation.
   - Issues a decision to:
     - Approve.
     - Approve with conditions.
     - Reject.
     - Defer.

2. The decision is captured as a **DecisionLogEntry** that references:

   - ChangeRequest ID.
   - Affected CIs and baselines.
   - Any conditions or constraints on implementation.

### 7.6 Step 6 – Plan and Implement Approved Changes

For approved ChangeRequests:

1. The System 1 Owner and Configuration / Document Controller plan the implementation:

   - Identify the specific edits or updates required.
   - Assign responsibility for making the changes (for example document authors, model maintainers).
   - Determine whether a new BaselineRecord will be created or an existing one updated after implementation.

2. Changes are implemented in the repository according to:

   - `ERAGS-MOD-CONF-003_Repository_Metadata_and_Git_Workflow_Model.md` (branching, commits, pull requests, review).

3. For significant changes:

   - A feature branch or change-specific branch may be used.
   - Peer review is performed before merging.

4. GovernanceDocumentMetadata and CI register entries are updated to reflect:

   - New versions.
   - Status changes (for example Draft → UnderReview → Approved).
   - Links to the ChangeRequest and DecisionLogEntry.

### 7.7 Step 7 – Verification and Validation

After implementation:

1. The Configuration / Document Controller and System 1 Owner verify that:

   - All intended artefacts have been updated correctly.
   - No unintended changes have been introduced.

2. If the change relates to:

   - Requirements or RTM:
     - Check that traceability is consistent and that there are no orphaned or dangling references.
   - KPI models:
     - Confirm that KPI calculations still run correctly, and thresholds are consistent.
   - Policies or strategies:
     - Confirm alignment between texts, metadata and linked models.

3. Results of verification are recorded in a **Change Verification Note** linked to the ChangeRequest.

### 7.8 Step 8 – Update Baselines and Close ChangeRequest

1. If the change affects the reference state of System 1:

   - A BaselineRecord is created or updated in line with `ERAGS-MOD-CONF-001` and `ERAGS-MOD-CONF-002`.
   - The associated Git tag is applied if defined in the Git workflow model.

2. The ChangeRequest is then:

   - Marked as **Implemented** and then **Closed** once verification and baseline updates are complete.
   - Status and closing notes are recorded.

3. Any follow-up actions (for example communication, training) are documented and handed to the relevant owners.

## 8. Outputs and Records

Key outputs and records of this process include:

1. **ChangeRequest**
   - Core record of the requested change, trigger, justification and affected CIs.

2. **Change Impact Note**
   - Summary of impact analysis.

3. **CRG Recommendation Record**
   - Recommendation and rationale from the ChangeReviewGroup.

4. **DecisionLogEntry**
   - Formal approval decision and conditions.

5. **Updated CIs and GovernanceDocumentMetadata**
   - Documents, models, requirements and metadata updated in line with the change.

6. **Change Verification Note**
   - Evidence of verification that changes were implemented correctly.

7. **BaselineRecord updates**
   - Where baselines are created or updated due to the change.

These artefacts provide end-to-end traceability from change trigger through to implementation and verification.

## 9. Interfaces with Other Processes

This SOP interfaces with:

- **ERAGS-PROC-001_Strategy_and_Governance_Review_Process**
  - Provides change triggers via governance decisions.
  - Receives confirmation that decisions have been implemented in artefacts.

- **ERAGS-PROC-002_Programme_Governance_SOP**
  - Programme decisions may require updates to strategy, requirements or models.

- **ERAGS-PROC-003_Performance_and_KPI_Review_SOP**
  - Changes to KPI definitions or thresholds are managed via this SOP.

- **ERAGS-PROC-004_Policy_Management_SOP**
  - Policy text and metadata changes are controlled here.

- **ERAGS-PROC-006_Document_Lifecycle_and_Baseline_Management_SOP**
  - Coordinates lifecycle states and baselines as part of change implementation.

- **ERAGS-PROC-007_Data_Integration_and_Quality_Checks_SOP**
  - Ensures that CI changes affecting data models or flows are consistent with how data is integrated.

- **ERAGS-PROC-008_Incident_Driven_Governance_Intervention_SOP**
  - Incident responses may result in urgent ChangeRequests.

## 10. Metrics and Effectiveness Checks

Effectiveness of Change Control can be assessed using:

1. **Process performance**
   - Number of ChangeRequests raised, implemented, rejected and deferred.
   - Average time from ChangeRequest submission to decision.
   - Average time from approval to implementation and closure.

2. **Traceability**
   - Ability to trace each implemented change back to:
     - Triggering decision or event.
     - Impact analysis.
     - Approval decision.

3. **Configuration integrity**
   - Frequency of configuration-related errors found in audits or QA checks.
   - Number of unapproved or undocumented changes detected.

4. **Baseline stability**
   - Reasonableness of baseline frequency:
     - Neither too frequent (noise) nor too rare (poor control).

These measures can be formalised as QA checks under `/qa`.

## 11. Compliance and Audit Considerations

Auditors should be able to:

- List all ChangeRequests in a given period with their status.
- For sampled changes, retrieve:
  - ChangeRequest record.
  - Change Impact Note.
  - CRG recommendation.
  - DecisionLogEntry.
  - Evidence of implemented updates (documents, models, metadata).
  - Change Verification Note.
  - Associated BaselineRecord adjustments.
- Confirm that:
  - Changes to governance CIs followed this process.
  - No significant changes have bypassed change control.
  - Lifecycle states and Git tags/branches match the documented configuration state.

This completes the definition of ERAGS-PROC-005 Change Control SOP.
