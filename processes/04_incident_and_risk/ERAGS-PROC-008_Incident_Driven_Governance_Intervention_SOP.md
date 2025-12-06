---
DocID: ERAGS-PROC-008
Title: Incident-Driven Governance Intervention SOP
Version: 0.1
Status: Draft
OwnerRole: Electrical Engineer – Roads Electrical Sub-Section (System 1 Owner)
OwnerName: Fani Masoabi
ApproverRole: Director – Roads Network Maintenance
ApproverName: (to be designated)
CreatedDate: 2025-12-05
LastUpdatedDate: 2025-12-05
System: ERAGS (Electrical Roads Asset Governance & Strategy System)
ProcessFamily: IncidentAndRisk
RelatedModels:
  - ERAGS-MOD-ARCH-001_System_Context_Diagram.md
  - ERAGS-MOD-ARCH-002_Logical_Architecture.md
  - ERAGS-MOD-ARCH-003_Component_Responsibilities_View.md
  - ERAGS-MOD-DATA-001_Governance_Data_Dictionary.md
  - ERAGS-MOD-DATA-002_Entity_Relationship_Model.md
  - ERAGS-MOD-FLOW-001_External_Information_Flows.md
  - ERAGS-MOD-FLOW-002_Internal_ERAGS_Information_Flows.md
  - ERAGS-MOD-KPI-001_KPI_Definitions_and_Structure.md
  - ERAGS-MOD-KPI-002_KPI_Calculation_and_Data_Lineage_Model.md
  - ERAGS-MOD-KPI-003_Governance_Decision_Rules_and_Thresholds_Model.md
RelatedDocs:
  - ERAGS-DOC-CTX-001
  - ERAGS-DOC-POL-001
  - ERAGS-DOC-STR-001
  - ERAGS-DOC-PROC-OV-001
  - ERAGS-DOC-STK-001
RelatedDataEntities:
  - IncidentSummary
  - KPIRecord
  - PerformanceSummary
  - ProgrammeRecord
  - DecisionLogEntry
  - GovernanceDocumentMetadata
  - DataQualityIssue
  - IncidentCase
ImplementsRequirements:
  - ERAGS-F-003
  - ERAGS-F-008
  - ERAGS-D-002
  - ERAGS-D-003
  - ERAGS-NF-006
  - ERAGS-R-001
  - ERAGS-R-003
---

# Incident-Driven Governance Intervention SOP  
*(ERAGS-PROC-008)*

## 1. Purpose

This Standard Operating Procedure defines how System 1 – ERAGS responds, at the **governance layer**, to serious incidents related to:

- Artificial road lights.
- Traffic signals and associated control systems.
- Other electrical and electronic roadside facilities.

The focus is on **governance interventions**, not on the immediate operational emergency response. The process ensures that:

- Serious incidents are systematically escalated into ERAGS.
- Their causes and implications are analysed from a governance perspective.
- Appropriate changes to policies, programmes, standards or governance processes are initiated.
- All interventions are traceable and auditable.

## 2. Scope

This SOP applies when incidents meet defined **severity and governance-relevance thresholds**, including:

- Road accidents where lighting or traffic signal performance is a suspected contributing factor.
- Serious safety incidents affecting staff, contractors or the public.
- Catastrophic or repeated failures of critical lighting or signalling infrastructure.
- Incidents revealing systemic vulnerabilities (for example widespread vandalism/theft, recurring control failures).

Out of scope:

- Routine, low-severity operational faults handled purely via CMMS/WFM processes.
- Non-electrical incidents unrelated to roads electrical assets.

The operational emergency response (for example callout of technicians, traffic control, emergency services) is assumed to follow separate operational procedures; this SOP begins when an incident is identified as **governance-relevant**.

## 3. Definitions

For the purposes of this SOP:

- **Incident**: Any unplanned event involving roads electrical assets resulting in, or having potential for, harm to people, property, service levels or compliance.
- **Governance-relevant Incident**: An incident whose severity, frequency, or pattern suggests the need for changes at policy, programme, standards or strategy level.
- **IncidentCase**: A governance-level case record in ERAGS that collates information, analysis, decisions and actions for a given governance-relevant incident or cluster of incidents.

## 4. Roles and Responsibilities

(Aligned with ERAGS-DOC-STK-001.)

- **Electrical Engineer – Roads Electrical Sub-Section (System 1 Owner)**
  - Owns the Incident-Driven Governance Intervention SOP.
  - Decides whether incidents are governance-relevant.
  - Coordinates analysis and governance intervention options.
  - Ensures follow-through into programmes, policies or change control.

- **HSE Representative**
  - Leads safety and risk interpretation of incidents.
  - Ensures incident handling aligns with health and safety legislation and standards.
  - Advises on risk controls and mitigations.

- **Governance and Performance Analyst**
  - Integrates incidents into IncidentSummary, KPIRecord and PerformanceSummary.
  - Analyses patterns and quantitative impacts.
  - Documents data-related limitations.

- **Operations / Maintenance Representative**
  - Provides factual account of operational response.
  - Shares insights into failure modes and field conditions.

- **Technical Standards/Engineering Representative**
  - Assesses implications for design, specification and technical standards.
  - Proposes technical mitigations where appropriate.

- **Director – Roads Network Maintenance**
  - Approves governance-level interventions where required (policy, programme, major standards changes).
  - Ensures alignment with organisational risk appetite and strategy.

- **Configuration / Document Controller**
  - Ensures decisions, actions and resulting document/model updates are captured under change control and lifecycle management.

## 5. Inputs

1. **Incident data and reports**
   - Source operational incident/fault reports.
   - HSE investigation reports (where available).
   - Witness statements or operational logs (if relevant).

2. **Integrated ERAGS data**
   - IncidentSummary (from ERAGS-PROC-007).
   - PerformanceSummary and KPIRecord for relevant periods and areas.

3. **Context and governance documents**
   - ERAGS context, policy and strategy:
     - `ERAGS-DOC-CTX-001`
     - `ERAGS-DOC-POL-001`
     - `ERAGS-DOC-STR-001`
   - Relevant standards and design criteria (referenced via GovernanceDocumentMetadata and any StandardsRegister mechanisms).

4. **Previous decisions and actions**
   - DecisionLogEntry records related to similar incidents or risks.
   - ProgrammeRecord entries for programmes already addressing the area/issue.

5. **Data quality context**
   - DataQualityIssue entries related to incident or performance data impacting interpretation.

## 6. Pre-Conditions

Before invoking full governance intervention:

1. The incident has been recorded in the operational incident/fault systems as per their procedures.
2. Immediate safety and operational stabilisation has been carried out (for example making equipment safe, restoring basic signalling, temporary controls).
3. Enough information is available to make at least a preliminary assessment:
   - Basic facts: when, where, what, who was involved.
   - Preliminary severity and potential link to roads electrical assets.
4. The System 1 Owner and HSE Representative jointly confirm that the incident is **governance-relevant** (or that a cluster of similar incidents collectively is).

## 7. Procedure

### 7.1 Step 1 – Identify Governance-Relevant Incident and Open IncidentCase

1. When a potential governance-relevant incident is detected (either individually or as part of a pattern):

   - The System 1 Owner and HSE Representative perform a quick screening.
   - Criteria may include:
     - Fatality or serious injury.
     - Major traffic disruption.
     - Repeated failures at the same location.
     - Evidence of systemic design or procedural weaknesses.

2. If confirmed:

   - An **IncidentCase** record is created with:
     - IncidentCaseID (unique).
     - Link(s) to operational incident IDs.
     - Location, date/time and asset types.
     - Initial classification (for example SafetyCritical, OperationalCritical, ReputationalRisk).
     - Short description.

3. The IncidentCase is linked to:

   - Relevant IncidentSummary entries.
   - Preliminary KPI impacts where visible.

### 7.2 Step 2 – Collect and Consolidate Incident Information

The System 1 Owner coordinates with Operations, HSE and the Analyst to gather:

1. **Operational incident information**
   - What occurred, sequence of events.
   - Equipment involved (assets, controllers, cabling, etc.).
   - Environmental conditions (weather, time of day).
   - Prior maintenance history or known issues at the location.

2. **Safety and HSE information**
   - Injury or fatality details (kept according to HSE privacy/confidentiality rules).
   - HSE investigation or preliminary findings.

3. **Data integration context**
   - Confirm that incident is captured in IncidentSummary.
   - Note any DataQualityIssue entries affecting this incident or related metrics.

4. **Historical and contextual data**
   - Previous incidents at the same location or similar configurations.
   - Relevant KPIs (for example incident-related KPIs, availability, MTTR) around this area.

All of this is summarised in an **IncidentCase Fact Pack**, referenced by the IncidentCase record.

### 7.3 Step 3 – Classify Incident and Determine Governance Questions

1. The System 1 Owner and HSE Representative classify the incident along dimensions such as:

   - Type (for example signal failure, lighting outage, electrical shock, vandalism/theft-related).
   - Severity (for example S1 – Catastrophic, S2 – Major, S3 – Moderate, S4 – Minor).
   - Recurrence (single event vs repeated pattern).
   - Governance implications (for example policy gap, design weakness, implementation issue).

2. Based on classification, they identify key **governance questions**, for example:

   - Are current policies and design standards adequate for this context?
   - Is there a need for a targeted programme (for example asset replacement, vandalism mitigation)?
   - Are maintenance and operational procedures sufficient?
   - Is incident and performance monitoring capturing risk early enough?

3. These questions are recorded in the IncidentCase, forming the basis for governance discussion.

### 7.4 Step 4 – Convene Incident Governance Review

1. For SafetyCritical or OperationalCritical incidents, the System 1 Owner convenes an **Incident Governance Review** meeting.

   - Participants:
     - Director – Roads Network Maintenance (for high-severity cases).
     - System 1 Owner.
     - HSE Representative.
     - Governance and Performance Analyst.
     - Operations / Maintenance Representative.
     - Technical Standards/Engineering Representative.
     - Others as needed (legal, communications, etc.).

2. The IncidentCase Fact Pack and governance questions are distributed prior to the meeting.

3. During the review, the group:

   - Confirms the facts and classification.
   - Explores plausible root causes (recognising that detailed root-cause investigations may occur in parallel via HSE/engineering processes).
   - Considers broader patterns (similar incidents elsewhere, KPI trends).
   - Identifies governance-level gaps or vulnerabilities.

### 7.5 Step 5 – Formulate Governance Interventions

Based on the review:

1. The group identifies potential **governance interventions**, for example:

   - Policy adjustments or creation of new policy clauses (ERAGS-PROC-004).
   - Initiation or modification of programmes (ERAGS-PROC-002).
   - Changes to design standards or technical configurations (via Change Control, ERAGS-PROC-005).
   - Enhancements to operational procedures (referenced from governance level, though operational SOPs themselves may live outside ERAGS).
   - Enhancements to monitoring and KPI definitions (for example new KPIs or thresholds in ERAGS-MOD-KPI-001/002/003).

2. For each potential intervention, the group considers:

   - Impact on safety and risk.
   - Implementation feasibility and time frame.
   - Resource and cost implications.
   - Consistency with policy and strategy.

3. The group agrees on a set of **recommended interventions**, each documented in the IncidentCase, with:

   - Description.
   - Intended effect.
   - Responsible role for follow-through.
   - Proposed target date or time frame.

### 7.6 Step 6 – Record Decisions and Trigger Downstream Processes

1. For interventions that require formal governance decisions:

   - The Director – Roads Network Maintenance (or designated authority) approves, modifies or rejects the recommendations.

2. Decisions are captured as **DecisionLogEntry** records that include:

   - Link to IncidentCaseID.
   - Summary of decision.
   - Linked interventions and responsible roles.
   - Any conditions or constraints.

3. Based on the type of intervention, downstream processes are initiated:

   - **Policy changes**:
     - Initiate or update PolicyChangeCase via ERAGS-PROC-004.
   - **Programmes**:
     - Create or update ProgrammeInitiationRecord via ERAGS-PROC-002.
   - **Changes to governance artefacts**:
     - Raise ChangeRequest via ERAGS-PROC-005.
   - **KPI and monitoring changes**:
     - Initiate review of KPI definitions/thresholds via ERAGS-PROC-003 and ERAGS-PROC-005.
   - **Data integration or classification changes**:
     - Propose updates in ERAGS-PROC-007 and relevant data models.

4. The IncidentCase is updated to reflect which interventions have been initiated and through which processes.

### 7.7 Step 7 – Follow-Up, Monitoring and Closure

1. The System 1 Owner tracks progress of interventions linked to the IncidentCase:

   - Status of related ChangeRequests.
   - Status of policy or programme changes.
   - Implementation of any operational changes that were triggered at governance level.

2. Over an agreed monitoring period, the Governance and Performance Analyst:

   - Monitors KPIs and incident patterns related to the incident context.
   - Assesses whether interventions are having the expected impact (for example reduction in similar incidents).

3. The HSE Representative:

   - Confirms that any specific HSE recommendations have been implemented or integrated into governance artefacts where relevant.

4. Once key interventions are implemented and monitored for a reasonable period:

   - The System 1 Owner may recommend **closing** the IncidentCase at the governance level.
   - A brief **IncidentCase Closure Note** documents:
     - Summary of incident and interventions.
     - Observed impact (where measurable).
     - Any residual risks or open actions.

5. The IncidentCase status is set to Closed, but remains available for audit and future reference.

## 8. Outputs and Records

Key outputs and records from this SOP include:

1. **IncidentCase**
   - Core governance record for the incident, with links to incident data, KPIs, decisions and interventions.

2. **IncidentCase Fact Pack**
   - Consolidated information used for governance review.

3. **Governance classification and questions**
   - Documented understanding of severity, patterns and governance concerns.

4. **Incident Governance Review notes**
   - Minutes or structured notes capturing discussions and considerations.

5. **DecisionLogEntry records**
   - Formal governance decisions related to the incident.

6. **Linked artefacts**
   - PolicyChangeCase references.
   - ProgrammeInitiationRecord references.
   - ChangeRequest references.
   - KPI or monitoring changes (where applicable).

7. **IncidentCase Closure Note**
   - Summary of interventions and outcomes once the case is closed.

These records provide a complete trace from incident occurrence to governance-level response and follow-through.

## 9. Interfaces with Other Processes

This SOP interfaces with:

- **ERAGS-PROC-007_Data_Integration_and_Quality_Checks_SOP**
  - Ensures incident data is correctly integrated and quality-checked before governance analysis.

- **ERAGS-PROC-003_Performance_and_KPI_Review_SOP**
  - Incident patterns and related KPIs are reviewed in routine KPI reviews; some IncidentCases may originate from these patterns.

- **ERAGS-PROC-001_Strategy_and_Governance_Review_Process**
  - Serious or repeated incidents may be escalated into strategic and governance reviews.

- **ERAGS-PROC-002_Programme_Governance_SOP**
  - Incident-driven interventions may result in new or adjusted programmes.

- **ERAGS-PROC-004_Policy_Management_SOP**
  - Incidents may reveal policy gaps and drive policy change.

- **ERAGS-PROC-005_Change_Control_SOP**
  - Changes to governance artefacts arising from IncidentCases must follow change control.

- **ERAGS-PROC-006_Document_Lifecycle_and_Baseline_Management_SOP**
  - Incident-driven changes may affect baselines and document lifecycle states.

## 10. Metrics and Effectiveness Checks

Effectiveness of incident-driven governance interventions can be assessed via:

1. **Coverage and responsiveness**
   - Number of governance-relevant IncidentCases opened per period.
   - Time from incident occurrence to IncidentCase opening and to governance review.

2. **Traceability**
   - Ability to trace from a major incident to:
     - IncidentCase.
     - Governance decisions.
     - Resulting changes to policies, programmes or standards.

3. **Risk reduction**
   - Trends in recurrence of similar incidents after interventions.
   - Trends in safety- and incident-related KPIs.

4. **Timeliness of implementation**
   - Time from governance decision to implementation of key interventions.

5. **Audit findings**
   - Frequency and severity of audit observations related to incident handling at the governance level.

These indicators can be formalised in QA artefacts under `/qa`.

## 11. Compliance and Audit Considerations

Auditors should be able to:

- Identify all governance-relevant IncidentCases in a given period.
- For sampled incidents, retrieve:
  - IncidentCase record and Fact Pack.
  - Evidence of classification and governance questions.
  - Incident Governance Review notes.
  - DecisionLogEntry records and linked downstream processes.
  - IncidentCase Closure Note and evidence of changes implemented.

- Confirm that:
  - Serious incidents are not handled only operationally, but also receive appropriate governance attention.
  - Incident-driven changes are integrated into policies, programmes, standards and monitoring via the defined ERAGS processes.
  - The governance response is documented, traceable and aligned with legal, regulatory and safety obligations.

This completes the definition of ERAGS-PROC-008 Incident-Driven Governance Intervention SOP.
