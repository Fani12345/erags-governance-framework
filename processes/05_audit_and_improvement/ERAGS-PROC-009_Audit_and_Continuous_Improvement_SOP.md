---
DocID: ERAGS-PROC-009
Title: Audit and Continuous Improvement SOP
Version: 0.1
Status: Draft
OwnerRole: Electrical Engineer – Roads Electrical Sub-Section (System 1 Owner)
OwnerName: Fani Masoabi
ApproverRole: Director – Roads Network Maintenance
ApproverName: (to be designated)
CreatedDate: 2025-12-05
LastUpdatedDate: 2025-12-05
System: ERAGS (Electrical Roads Asset Governance & Strategy System)
ProcessFamily: AuditAndImprovement
RelatedModels:
  - ERAGS-MOD-ARCH-001_System_Context_Diagram.md
  - ERAGS-MOD-ARCH-002_Logical_Architecture.md
  - ERAGS-MOD-ARCH-003_Component_Responsibilities_View.md
  - ERAGS-MOD-DATA-001_Governance_Data_Dictionary.md
  - ERAGS-MOD-DATA-002_Entity_Relationship_Model.md
  - ERAGS-MOD-DATA-003_Document_Metadata_Model.md
  - ERAGS-MOD-FLOW-002_Internal_ERAGS_Information_Flows.md
  - ERAGS-MOD-KPI-001_KPI_Definitions_and_Structure.md
  - ERAGS-MOD-KPI-002_KPI_Calculation_and_Data_Lineage_Model.md
  - ERAGS-MOD-KPI-003_Governance_Decision_Rules_and_Thresholds_Model.md
  - ERAGS-MOD-CONF-001_Configuration_Item_And_Baseline_Model.md
  - ERAGS-MOD-CONF-002_Governance_Document_Lifecycle_Model.md
  - ERAGS-MOD-CONF-003_Repository_Metadata_and_Git_Workflow_Model.md
RelatedDocs:
  - ERAGS-DOC-CTX-001
  - ERAGS-DOC-POL-001
  - ERAGS-DOC-STR-001
  - ERAGS-DOC-OV-000
  - ERAGS-DOC-PROC-OV-001
  - ERAGS-DOC-STK-001
RelatedDataEntities:
  - GovernanceDocumentMetadata
  - KPIRecord
  - PerformanceSummary
  - IncidentSummary
  - ProgrammeRecord
  - BaselineRecord
  - ChangeRequest
  - DataQualityIssue
  - AuditPlan
  - AuditChecklist
  - AuditFinding
  - ImprovementAction
  - QARecord
ImplementsRequirements:
  - ERAGS-F-003
  - ERAGS-F-005
  - ERAGS-F-009
  - ERAGS-D-001
  - ERAGS-D-002
  - ERAGS-D-003
  - ERAGS-D-004
  - ERAGS-NF-001
  - ERAGS-NF-002
  - ERAGS-NF-003
  - ERAGS-NF-006
  - ERAGS-R-001
  - ERAGS-R-002
  - ERAGS-R-003
---

# Audit and Continuous Improvement SOP  
*(ERAGS-PROC-009)*

## 1. Purpose

This Standard Operating Procedure defines how System 1 – ERAGS:

- Plans and performs **internal audits** of governance artefacts and processes.
- Captures **audit findings** in a structured way.
- Drives **corrective and preventive actions** that improve:
  - Governance quality.
  - Data and KPI reliability.
  - Configuration and document control.
  - Overall maturity of the roads electrical governance framework.

The process closes the loop between design, operation and learning, ensuring that System 1 continuously improves rather than remaining static.

## 2. Scope

This SOP covers audits focused on System 1 – ERAGS itself, including:

- Governance processes (PROC-001 to PROC-008).
- Governance documents and models in:
  - `docs/`
  - `requirements/`
  - `models/`
  - `processes/`
  - `qa/` (where governance-related).
- Data and KPI handling for governance purposes.
- Configuration and baseline control of System 1 artefacts.

It does not replace:

- Technical audits of field installations (although it may reference their results).
- Corporate-wide audits run under broader quality management systems (though it may align with them and provide evidence).

## 3. Audit Types

Typical audits under this SOP include:

1. **Process conformance audits**
   - Check whether governance processes (for example Strategy Review, Programme Governance, Change Control) are followed as documented.

2. **Document and configuration audits**
   - Check that documents, models and baselines:
     - Follow naming and metadata conventions.
     - Have correct lifecycle states.
     - Are aligned with change records and baselines.

3. **Data and KPI audits**
   - Check that data used for governance:
     - Follows the data models.
     - Has been integrated and quality-checked.
     - Produces KPIs consistent with definitions and thresholds.

4. **Thematic improvement audits**
   - Deep dives into specific themes (for example incident handling, programme traceability, policy updates).

## 4. Roles and Responsibilities

- **Electrical Engineer – Roads Electrical Sub-Section (System 1 Owner)**
  - Owns the Audit and Continuous Improvement process.
  - Approves audit plans and priorities.
  - Ensures that audit findings are addressed appropriately.

- **Internal Auditor / QA Lead (can be a designated role)**
  - Plans and conducts audits.
  - Maintains AuditPlan, AuditChecklist and AuditFinding records.
  - Ensures independence where possible (for example not auditing work they authored).

- **Governance and Performance Analyst**
  - Supports audits related to data and KPI handling.
  - Provides evidence and clarifications.

- **Configuration / Document Controller**
  - Supports audits related to document and configuration control.
  - Provides CI register and BaselineRecord information.

- **Process Owners (for PROC-001 to PROC-008)**
  - Provide evidence of process execution (records, minutes, artefacts).
  - Implement corrective and preventive actions within their domains.

- **Director – Roads Network Maintenance**
  - Reviews major audit results and improvement themes.
  - Approves high-level improvement priorities if required.

## 5. Inputs

1. **AuditPlan**
   - Planned audits for the period (for example annual or bi-annual plan).
   - Scope, frequency and priorities.

2. **Applicable governance artefacts**
   - Documents, models, processes in the ERAGS repository.
   - CI register and BaselineRecord entries.

3. **Past audit and QA records**
   - Previous AuditFinding and ImprovementAction entries.
   - QA checks and DataQualityIssue logs.

4. **Performance and incident context**
   - KPIRecord, PerformanceSummary, IncidentSummary.
   - Information on specific issues that may warrant focused audits.

5. **External requirements**
   - Corporate, regulatory or standards-based audit expectations (if any).

## 6. Pre-Conditions

Before conducting audits for a period:

1. The System 1 Owner and Internal Auditor must agree on:

   - The AuditPlan for the period.
   - Any high-priority themes (for example following a major incident or audit finding).

2. The Configuration / Document Controller must confirm:

   - Availability of up-to-date CI register and BaselineRecord entries.

3. For data/KPI audits:

   - Confirm that IntegrationRun and DataQualityIssue records exist for the periods being audited (ERAGS-PROC-007).

## 7. Procedure – Audit Planning

### 7.1 Step 1 – Define AuditPlan

1. The Internal Auditor drafts an **AuditPlan** for the period (for example one year), specifying:

   - Planned audits (ID, title, scope, type).
   - Tentative schedule.
   - Responsible auditor(s).
   - Priority or risk weighting.

2. Audits should cover, over time:

   - All core governance processes.
   - A representative sample of documents, models and baselines.
   - Key data flows and KPIs.

3. The System 1 Owner reviews and approves the AuditPlan.

4. The plan is stored (for example under `qa/audit/ERAGS-AUD-PLAN-YYYY.md`) and referenced via GovernanceDocumentMetadata as needed.

### 7.2 Step 2 – Prepare AuditChecklist for Each Audit

For each planned audit:

1. The Internal Auditor prepares an **AuditChecklist** that:

   - Defines audit objectives and criteria.
   - Lists specific checks to be performed.
   - Identifies evidence to be reviewed (for example specific documents, logs, records).

2. The checklist may be standardised for recurring audits (for example Change Control audit, Data/KPI audit).

## 8. Procedure – Conducting an Audit

### 8.1 Step 3 – Notify Stakeholders

1. The Internal Auditor informs relevant stakeholders (for example process owners, System 1 Owner, Document Controller) of:

   - Audit scope and objectives.
   - Date/time and expected duration.
   - Information and evidence required.

### 8.2 Step 4 – Collect Evidence

1. The Internal Auditor collects evidence, which may include:

   - Documents and models in the repository.
   - Meeting minutes and DecisionLogEntry records.
   - IntegrationRun and DataQualityIssue logs.
   - RTM and traceability checks.
   - CI register and BaselineRecord information.

2. Evidence collection should be systematic and traceable to the AuditChecklist items.

### 8.3 Step 5 – Perform Checks Against Criteria

For each checklist item:

1. The Internal Auditor assesses:

   - Conformance:
     - Does practice match what is defined in SOPs, policies and models?
   - Completeness:
     - Are all required artefacts present and complete?
   - Accuracy:
     - Are records and metadata accurate and up to date?
   - Effectiveness:
     - Does the process or artefact support governance objectives (for example traceability, data quality, compliance)?

2. Where sampling is used (for example sampling ChangeRequests or IncidentCases), sampling method and sample size should be documented.

### 8.4 Step 6 – Record AuditFindings

1. Each non-conformance, observation or improvement opportunity is recorded as an **AuditFinding** with:

   - FindingID (unique).
   - AuditID (link to specific audit).
   - Category (for example Non-conformance, Observation, Opportunity for Improvement, Good Practice).
   - Severity (for example Minor, Major, Critical).
   - Description.
   - Criteria reference (for example specific clause in a SOP or policy).
   - Evidence reference (for example file path, meeting date).
   - Suggested corrective or preventive action(s).

2. Where no significant issues are found for a checklist item, this positive result may be recorded as evidence of compliance.

### 8.5 Step 7 – Prepare Audit Report

1. The Internal Auditor prepares an **Audit Report** or summary that includes:

   - Scope, objectives and criteria.
   - Date and participants.
   - Summary of overall findings and conclusions.
   - Detailed list of AuditFindings.
   - Recommended ImprovementActions.

2. The report is shared with:

   - System 1 Owner.
   - Relevant process owners.
   - Director – Roads Network Maintenance (for significant audits or critical findings).

## 9. Procedure – ImprovementActions and Follow-Up

### 9.1 Step 8 – Define and Register ImprovementActions

1. For each AuditFinding that requires action, the System 1 Owner (with relevant process owners) defines one or more **ImprovementAction** entries:

   - ActionID.
   - Link to FindingID.
   - Description.
   - Type (Corrective, Preventive, Enhancing).
   - Responsible owner.
   - Target completion date.
   - Priority (for example High, Medium, Low).

2. Actions are registered in a central ImprovementAction log (for example under `qa/improvement/`).

### 9.2 Step 9 – Link to Change Control and Other Processes

1. Where actions affect governance artefacts:

   - **ChangeRequests** are raised via ERAGS-PROC-005.
   - Document lifecycle updates follow ERAGS-PROC-006.
   - Data model or integration changes follow ERAGS-PROC-007.
   - Policy or programme changes follow ERAGS-PROC-004 and ERAGS-PROC-002 respectively.

2. The ImprovementAction record references:

   - Associated ChangeRequest IDs.
   - Any DecisionLogEntry records (for major improvements).

### 9.3 Step 10 – Implement and Verify Improvements

1. Process owners implement actions and provide evidence of completion.

2. The Internal Auditor or System 1 Owner verifies implementation, checking that:

   - Changes have been made as specified.
   - Relevant records and metadata are updated.
   - Baselines are adjusted where appropriate.

3. Verification is recorded in the ImprovementAction log (for example “Verified” with date and verifier).

### 9.4 Step 11 – Close Findings and Actions

1. Once an ImprovementAction is verified:

   - The associated AuditFinding is marked as Closed.
   - Any related ChangeRequests are updated to reflect completion.

2. Where actions cannot be fully implemented, residual risks or constraints are documented and, if necessary, escalated via governance processes.

## 10. Continuous Improvement and Management Review

### 10.1 Step 12 – Periodic Review of Audit and Improvement Themes

1. On at least an annual basis (or aligned with organisational cadence), the System 1 Owner and Internal Auditor:

   - Review all AuditFindings and ImprovementActions over the period.
   - Identify recurring themes (for example repeated configuration issues, data quality weaknesses, process non-conformances).

2. These themes are consolidated into a **Continuous Improvement Summary**, which may include:

   - Root causes of recurring issues.
   - Systemic improvements proposed (for example training, additional SOPs, clearer roles, tooling upgrades).
   - Linkages to KPI trends and incident patterns.

### 10.2 Step 13 – Management Review

1. The Continuous Improvement Summary is presented to the Director – Roads Network Maintenance and relevant governance structures.

2. The management review should:

   - Confirm adequacy of the audit and improvement process.
   - Decide on major systemic changes or investments (for example new tools, additional resources).
   - Align continuous improvement priorities with strategy and risk appetite.

3. Any high-level decisions are recorded as DecisionLogEntry records and, where necessary, translated into:

   - Programmes (via ERAGS-PROC-002).
   - Policy changes (via ERAGS-PROC-004).
   - ChangeRequests (via ERAGS-PROC-005).

## 11. Outputs and Records

Key outputs and records include:

1. **AuditPlan**
   - Planned audits and priorities for the period.

2. **AuditChecklist**
   - Criteria and checks used in each audit.

3. **AuditFinding**
   - Structured record of each finding.

4. **Audit Reports / Summaries**
   - Narrative and tabular reports of audit results.

5. **ImprovementAction log**
   - Actions defined, implemented and verified.

6. **QARecord**
   - Any supporting quality assurance notes and confirmations.

7. **Continuous Improvement Summary**
   - Thematic overview of issues and improvements over time.

8. **DecisionLogEntry**
   - Management review decisions and major improvement commitments.

These records support traceability, accountability and demonstration of a functioning continuous improvement loop.

## 12. Interfaces with Other Processes

This SOP interfaces with:

- **ERAGS-PROC-001_Strategy_and_Governance_Review_Process**
  - Audit results and improvement themes may feed into strategic governance decisions.

- **ERAGS-PROC-002_Programme_Governance_SOP**
  - Some improvement actions may be implemented via programmes.

- **ERAGS-PROC-003_Performance_and_KPI_Review_SOP**
  - KPI and performance audits verify accuracy and effectiveness of KPI processes.

- **ERAGS-PROC-004_Policy_Management_SOP**
  - Policy-related findings translate into policy change cases.

- **ERAGS-PROC-005_Change_Control_SOP**
  - Many improvements require updates to governance artefacts via change control.

- **ERAGS-PROC-006_Document_Lifecycle_and_Baseline_Management_SOP**
  - Audits check and improve lifecycle and baseline accuracy.

- **ERAGS-PROC-007_Data_Integration_and_Quality_Checks_SOP**
  - Data and integration audits reinforce data quality processes.

- **ERAGS-PROC-008_Incident_Driven_Governance_Intervention_SOP**
  - Some audits may focus on the effectiveness of incident-driven interventions.

## 13. Metrics and Effectiveness Checks

Effectiveness of this SOP can be assessed using:

1. **Audit coverage**
   - Percentage of planned audits completed.
   - Coverage across processes, artefacts and data domains.

2. **Finding management**
   - Number of AuditFindings per period, by severity.
   - Percentage of findings with defined ImprovementActions.
   - Average time to close findings.

3. **Improvement impact**
   - Reduction in recurrence of similar findings over time.
   - Improvements in data quality and configuration integrity indicators.
   - Observed improvements in relevant KPIs or governance efficiency.

4. **Process health**
   - Feedback from process owners and management on usefulness of audits and improvements.

These metrics can later be formalised into QA dashboards or reports.

## 14. Compliance and Audit Considerations

External auditors or reviewers should be able to:

- Review the AuditPlan and confirm that it is appropriate for the risks and scope of System 1.
- Select specific audits and see:
  - AuditChecklist, evidence, AuditFindings and Audit Report.
  - Associated ImprovementActions and their status.
- Confirm that:
  - Significant findings are not left open indefinitely.
  - Systemic issues lead to changes in governance artefacts or practices via defined processes.
  - Continuous improvement is visible and traceable over time.

This completes the definition of ERAGS-PROC-009 Audit and Continuous Improvement SOP.
