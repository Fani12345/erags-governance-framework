---
DocID: ERAGS-PROC-004
Title: Policy Management SOP
Version: 0.1
Status: Draft
OwnerRole: Electrical Engineer – Roads Electrical Sub-Section (System 1 Owner)
OwnerName: Fani Masoabi
ApproverRole: Director – Roads Network Maintenance
ApproverName: (to be designated)
CreatedDate: 2025-12-05
LastUpdatedDate: 2025-12-05
System: ERAGS (Electrical Roads Asset Governance & Strategy System)
ProcessFamily: GovernanceCore
RelatedModels:
  - ERAGS-MOD-PROC-002
  - ERAGS-MOD-ARCH-001
  - ERAGS-MOD-ARCH-002
  - ERAGS-MOD-ARCH-003
  - ERAGS-MOD-DATA-001
  - ERAGS-MOD-DATA-003
  - ERAGS-MOD-FLOW-001
  - ERAGS-MOD-FLOW-002
  - ERAGS-MOD-CONF-001
  - ERAGS-MOD-CONF-002
  - ERAGS-MOD-CONF-003
RelatedDocs:
  - ERAGS-DOC-CTX-001
  - ERAGS-DOC-POL-001
  - ERAGS-DOC-STR-001
  - ERAGS-DOC-PROC-OV-001
  - ERAGS-DOC-STK-001
RelatedDataEntities:
  - GovernanceDocumentMetadata
  - StandardsRegister
  - DecisionLogEntry
  - KPIRecord
  - IncidentSummary
ImplementsRequirements:
  - ERAGS-F-001
  - ERAGS-F-003
  - ERAGS-F-009
  - ERAGS-D-004
  - ERAGS-R-001
  - ERAGS-R-002
  - ERAGS-R-003
  - ERAGS-NF-001
  - ERAGS-NF-003
---

# Policy Management SOP  
*(ERAGS-PROC-004)*

## 1. Purpose

This Standard Operating Procedure defines how System 1 – ERAGS manages the **lifecycle of governance policies** for:

- Artificial road lights.
- Traffic signals.
- Associated electrical and electronic facilities.

The process ensures that:

- Policies are grounded in legal, regulatory and contextual requirements.
- Policies are consistent with strategy and standards.
- Policy changes are controlled, traceable and auditable.
- Policy documents and their metadata are managed under configuration control and linked to baselines.

## 2. Scope

This SOP covers governance-level policies that:

- Define principles and rules for the planning, design, operation and maintenance of electrical roads assets.
- Apply across the national roads network or significant portions of it.

Examples:

- Policy on minimum lighting levels and hours of operation.
- Policy on traffic signal fail-safe behaviour.
- Policy on energy efficiency and technology selection (for example LED vs legacy technologies).
- Policy on vandalism/theft mitigation measures and response.

Out of scope:

- Detailed technical standards or design specifications (they may be referenced by policy and managed via standards management processes).
- Operational instructions specific to a single depot or contractor (unless explicitly elevated to policy level).

## 3. Triggers

Policy Management activities are triggered by:

1. **Governance decisions**
   - From Strategy and Governance Review (ERAGS-PROC-001).
   - From Programme Governance (ERAGS-PROC-002).
   - From Incident-Driven Governance Intervention (ERAGS-PROC-008).

2. **Regulatory or legal changes**
   - New or updated legislation, regulations or technical standards.

3. **Performance and risk evidence**
   - Persistent KPI deviations.
   - Repeated or severe incidents that indicate policy gaps.

4. **Periodic policy review**
   - Time-based reviews (for example every 3–5 years or as locally required).

Each policy change initiative begins with a **PolicyChangeInitiationRecord** linked to a DecisionLogEntry.

## 4. Roles and Responsibilities

(Aligned with ERAGS-DOC-STK-001.)

- **Director – Roads Network Maintenance**
  - Policy approver.
  - Ensures policies remain aligned with higher-level organisational and national directives.

- **Electrical Engineer – Roads Electrical Sub-Section (System 1 Owner)**
  - Owns the Policy Management process.
  - Coordinates drafting, review and change control for policies.
  - Ensures integration with strategy, programmes and performance evidence.

- **Legal/Regulatory Representative**
  - Interprets legislation, regulations and standards.
  - Ensures policy content is legally and regulatorily sound.

- **Technical Standards/Engineering Representative**
  - Ensures policies are technically coherent with applicable standards.
  - Advises on impacts to design and operational practices.

- **Governance and Performance Analyst**
  - Provides performance, KPI and incident evidence that motivates policy changes.
  - Evaluates potential impact of policy shifts on KPIs.

- **HSE Representative**
  - Ensures that safety-related policies address incident patterns and risk.

- **Configuration / Document Controller**
  - Manages policy document metadata and lifecycle states.
  - Ensures policy documents are correctly baselined and archived.

## 5. Inputs

1. **Context and strategy**
   - `ERAGS-DOC-CTX-001` (context).
   - `ERAGS-DOC-STR-001` (strategy).
   - Existing policy framework (`ERAGS-DOC-POL-001` and related policy documents).

2. **Legal and regulatory references**
   - National legislation, regulations and technical standards (referenced through the StandardsRegister entity).

3. **Performance and incident evidence**
   - KPIRecord.
   - PerformanceSummary.
   - IncidentSummary.
   - Any relevant thematic analyses (for example theft trends, failure modes).

4. **DecisionLogEntry and triggers**
   - Governance decisions that call for policy introduction, review or revision.
   - Policy review schedule (if periodic).

5. **Existing policy documents and metadata**
   - GovernanceDocumentMetadata for all active and relevant policies.
   - Previous versions (for reference where necessary).

## 6. Pre-Conditions

Before commencing a formal policy review or change:

1. The System 1 Owner must:

   - Identify clearly the policy or policy area in scope.
   - Confirm the trigger (for example decision ID, regulatory change, periodic review).

2. The Configuration / Document Controller must:

   - Confirm the current Approved policy version(s) and their lifecycle status.
   - Identify any related documents (for example strategies, standards) that may be affected.

3. The Legal/Regulatory Representative must:

   - Provide or confirm the list of applicable regulations and standards to be considered.

4. Data preparation:

   - The Governance and Performance Analyst should ensure relevant performance and incident data is available and QA’d via PROC-007 where used to justify policy changes.

## 7. Procedure

### 7.1 Step 1 – Initiate Policy Change or Review

1. The System 1 Owner logs a **PolicyChangeInitiationRecord** containing:

   - Trigger (decision, regulatory change, periodic review, performance/incident evidence).
   - Policy or policy area affected.
   - High-level objectives of the policy change (for example improved safety, energy efficiency, compliance).

2. A **PolicyChangeCase** is opened, with a unique ID, linked to:

   - DecisionLogEntry.
   - Relevant KPI and incident data.
   - StandardsRegister entries (for regulatory/standard changes).

### 7.2 Step 2 – Gather Evidence and Constraints

The System 1 Owner, working with the Analyst, Legal/Regulatory and Technical Standards roles:

1. Collects:

   - Relevant KPIs and trends.
   - Incident summaries linked to the policy area.
   - Any documented operational issues or lessons learned.

2. Summarises regulatory and standards context:

   - Applicable legislation.
   - Mandatory standards.
   - Recommended or best-practice guidelines.

3. Records any constraints:

   - Resource or funding limitations.
   - Implementation feasibility concerns.
   - Dependencies on other policy or strategy elements.

This is documented as a **Policy Evidence and Context Note**.

### 7.3 Step 3 – Draft or Revise Policy Content

1. The System 1 Owner, with input from the Technical Standards and HSE representatives, drafts:

   - New policy content (for new policies), or
   - Revised content for existing policies (redlines or tracked changes recommended).

2. Draft content must:

   - State clearly the **policy objective**.
   - Identify scope (assets, locations, time frames).
   - Specify **rules and principles**, not detailed step-by-step procedures.
   - Reference relevant standards and regulations where applicable.
   - Explicitly identify any changes to existing practice.

3. Policy draft metadata is updated:

   - Version (for example 0.1 for new draft, 1.1 for revision).
   - Status = Draft.
   - Links to PolicyChangeCase and evidence note.

4. The configuration model is followed:

   - CI identification consistent with ERAGS-MOD-CONF-001.
   - Lifecycle and version details aligned with ERAGS-MOD-CONF-002.

### 7.4 Step 4 – Internal Review and Refinement

1. The draft policy is circulated to:

   - Legal/Regulatory Representative.
   - Technical Standards/Engineering Representative.
   - HSE Representative.
   - Governance and Performance Analyst.
   - Any affected operational stakeholders or subject-matter experts.

2. Reviewers:

   - Check for legal/regulatory compliance.
   - Verify technical soundness and feasibility.
   - Assess safety implications.
   - Consider anticipated impact on KPIs and programmes.

3. Comments and requested changes are logged, preferably in a structured way (for example review log or tracked change record).

4. The System 1 Owner incorporates agreed changes and:

   - Updates the draft version number as necessary (for example 0.2, 0.3).
   - Sets Status = UnderReview once the draft is stable enough for formal approval.

### 7.5 Step 5 – Formal Approval

1. The final UnderReview version is tabled for approval with the Director – Roads Network Maintenance (and any formal policy governance forum as required).

2. The approval package includes:

   - Final draft policy text.
   - Policy Evidence and Context Note.
   - Summary of review comments and how they were resolved.
   - Description of anticipated impacts:
     - On KPIs.
     - On programmes.
     - On operational practices.

3. The approver may:

   - Approve as is.
   - Approve with minor conditions (to be incorporated into the final text).
   - Request further revisions (returning the document to Draft/UnderReview loop).
   - Reject the proposed policy change.

4. Approval decision and rationale are recorded as a **DecisionLogEntry**.

5. Upon approval:

   - Policy document Status = Approved.
   - Version is set to 1.0 (for new policies) or incremented appropriately for revisions (for example 2.0 for major revision, 1.1 for minor).

### 7.6 Step 6 – Update Baselines and Repository

The Configuration / Document Controller:

1. Updates GovernanceDocumentMetadata for the policy:

   - Status = Approved.
   - Version.
   - EffectiveDate (if applicable).
   - Supersedes / SupersededBy relationships where revisions are involved.

2. Ensures that:

   - Superseded policies are marked as Superseded or Archived as per ERAGS-MOD-CONF-002.
   - Baselines capturing the current policy framework are updated (per ERAGS-MOD-CONF-001).

3. Coordinates with Git workflow (ERAGS-MOD-CONF-003):

   - Ensures that the commit embodying the Approved policy is pushed to main.
   - Tags a baseline if this policy change is part of a major governance baseline.

### 7.7 Step 7 – Communicate and Implement Policy

1. The System 1 Owner prepares a **Policy Change Communication Note**, including:

   - Summary of changes.
   - Rationale and key evidence.
   - Effective date.
   - Implications for:
     - Design and standards.
     - Operations.
     - Programme planning.

2. The note is distributed to:

   - Relevant operational units and regional managers.
   - Programme and project teams.
   - Any other affected stakeholders.

3. Where implementation changes are required (for example operational procedures, design templates), the relevant structures initiate their own processes (outside this SOP), but the PolicyChangeCase tracks that these implementation actions have been launched.

### 7.8 Step 8 – Post-Implementation Review (Optional but Recommended)

After a suitable period:

1. The Governance and Performance Analyst and System 1 Owner review:

   - KPIs and incident patterns related to the policy area.
   - Feedback from operational staff and stakeholders.

2. Assess whether:

   - The policy is having the intended effect.
   - Unintended consequences are emerging.

3. If necessary, initiate another PolicyChangeCase to refine the policy.

## 8. Outputs and Records

Key outputs of this process are:

1. **PolicyChangeInitiationRecord**
   - Trigger and objectives for the policy change.

2. **Policy Evidence and Context Note**
   - Consolidated evidence base for policy decisions.

3. **Policy drafts and review logs**
   - Draft versions, comments and resolution notes.

4. **Approved policy document(s)**
   - With updated GovernanceDocumentMetadata.

5. **DecisionLogEntry records**
   - Approval decisions and key considerations.

6. **Updated StandardsRegister entries**
   - Where policy references or incorporates standards.

7. **Policy Change Communication Note**
   - For dissemination and implementation.

8. **Post-Implementation Review Notes** (where performed).

These provide traceable, auditable evidence for policy management activities.

## 9. Interfaces with Other Processes

This SOP interfaces with:

- **ERAGS-PROC-001_Strategy_and_Governance_Review_Process**
  - Provides and receives strategy-level decisions that may require policy change.

- **ERAGS-PROC-002_Programme_Governance_SOP**
  - Programmes may be used to implement policy changes.
  - Policy adjustments may arise from programme outcomes.

- **ERAGS-PROC-003_Performance_and_KPI_Review_SOP**
  - Performance and KPI evidence may identify areas needing policy adjustment.

- **ERAGS-PROC-005_Change_Control_SOP**
  - Formal change control mechanism for policy documents.

- **ERAGS-PROC-006_Document_Lifecycle_and_Baseline_Management_SOP**
  - Manages lifecycle states and baselines for policy documents.

- **ERAGS-PROC-007_Data_Integration_and_Quality_Checks_SOP**
  - Ensures that data used to justify policy change is of sufficient quality.

- **ERAGS-PROC-008_Incident_Driven_Governance_Intervention_SOP**
  - Major incidents may trigger urgent policy reviews.

## 10. Metrics and Effectiveness Checks

Effectiveness of Policy Management can be assessed through:

1. **Timeliness**
   - Percentage of scheduled policy reviews completed as planned.
   - Time from PolicyChangeInitiationRecord to approval or closure.

2. **Traceability**
   - Ability to trace from policy text to:
     - Legal/regulatory sources.
     - Performance and incident evidence.
     - Governance decisions.

3. **Implementation**
   - Evidence that policy changes are communicated and considered in:
     - Design standards.
     - Operational procedures.
     - Programme planning.

4. **Impact**
   - Changes in relevant KPIs and incident patterns after policy implementation.

These checks can later be formalised into QA artefacts under `/qa`.

## 11. Compliance and Audit Considerations

Auditors should be able to:

- Identify all policy change cases in a given period.
- For each case, retrieve:
  - PolicyChangeInitiationRecord.
  - Policy Evidence and Context Note.
  - Drafts and review comments.
  - Final Approved policy document and metadata.
  - DecisionLogEntry for approval.
  - Communication Note and any post-implementation review notes.
- Confirm that:
  - Lifecycle states and baselines were correctly updated.
  - Changes were carried out via the defined change control and configuration management processes.

This completes the definition of ERAGS-PROC-004 Policy Management SOP.
