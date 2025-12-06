---
DocID: ERAGS-PROC-002
Title: Programme Governance SOP
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
  - ERAGS-MOD-PROC-003
  - ERAGS-MOD-ARCH-001
  - ERAGS-MOD-ARCH-002
  - ERAGS-MOD-ARCH-003
  - ERAGS-MOD-DATA-001
  - ERAGS-MOD-DATA-002
  - ERAGS-MOD-FLOW-001
  - ERAGS-MOD-FLOW-002
  - ERAGS-MOD-KPI-001
  - ERAGS-MOD-KPI-002
  - ERAGS-MOD-KPI-003
RelatedDocs:
  - ERAGS-DOC-CTX-001
  - ERAGS-DOC-POL-001
  - ERAGS-DOC-STR-001
  - ERAGS-DOC-PROC-OV-001
  - ERAGS-DOC-STK-001
RelatedDataEntities:
  - ProgrammeRecord
  - Asset
  - PerformanceSummary
  - KPIRecord
  - IncidentSummary
  - EnergyCostSummary
  - DecisionLogEntry
  - GovernanceDocumentMetadata
ImplementsRequirements:
  - ERAGS-F-002
  - ERAGS-F-003
  - ERAGS-F-006
  - ERAGS-D-001
  - ERAGS-D-002
  - ERAGS-NF-002
  - ERAGS-NF-006
  - ERAGS-R-003
Alias:
  - PROC-Programme-Governance
---

# Programme Governance SOP  
*(ERAGS-PROC-002 / “PROC-Programme-Governance”)*

## 1. Purpose

This Standard Operating Procedure defines how investment and renewal **programmes** for electrical roads assets (artificial road lights, traffic signals and associated facilities) are:

- Identified and justified.
- Evaluated and prioritised.
- Approved and baselined.
- Monitored at the governance level.

The process ensures that programmes:

- Are grounded in strategy, performance gaps, risk, and regulatory requirements.
- Are aligned with available resources and constraints.
- Are traceable to decisions and evidence (data and analysis).

## 2. Scope

This process applies to all System 1 – ERAGS governance-level programmes that:

- Affect artificial road lights, traffic signals and associated facilities nationally or within defined areas/corridors.
- Require significant capital or operational expenditure and multi-year planning.
- Are governed at the level of the Director – Roads Network Maintenance and associated governance bodies.

Examples:

- LED retrofit programmes for specific corridors or regions.
- Traffic signal upgrade and standardisation programmes.
- Theft/vandalism mitigation programmes (for example cabling and cabinet protections).
- Smart control/telemetry rollout programmes.

Out of scope:

- Single, small maintenance actions or minor projects that do not constitute a formal programme (these are handled via operational work management systems).

## 3. Triggers

Programme Governance is initiated when:

1. **Strategic or governance review decisions**
   - From ERAGS-PROC-001, decisions such as:
     - “Initiate LED retrofit in high-energy-intensity corridors.”
     - “Develop a vandalism mitigation programme in high-incident areas.”

2. **Performance and KPI deviations**
   - Persistent KPI deviations beyond thresholds (ERAGS-MOD-KPI-003), indicating:
     - Structural shortcomings (for example ageing infrastructure, obsolete technology).
     - Need for targeted capital interventions.

3. **Regulatory or policy changes**
   - New requirements that demand systematic upgrades (for example new lighting standards).

4. **External funding opportunities**
   - Grants or budget allocations earmarked for specific interventions.

Each potential programme starts with a **ProgrammeInitiationRecord** linked to a DecisionLogEntry.

## 4. Roles and Responsibilities

(Aligned with ERAGS-DOC-STK-001.)

- **Director – Roads Network Maintenance**
  - Accountable for the programme portfolio.
  - Approves programme proposals and prioritisation.
  - Decides on funding allocation at the governance level.

- **Electrical Engineer – Roads Electrical Sub-Section (System 1 Owner)**
  - Owns the Programme Governance process within ERAGS.
  - Coordinates development and evaluation of programme proposals.
  - Ensures alignment with data-driven evidence and strategy.

- **Governance and Performance Analyst**
  - Provides analytical input:
    - Performance gaps.
    - KPI trends.
    - Risk and energy profiles.
  - Assists with defining benefits and expected impact.

- **Programme/Project Management Representative**
  - Advises on:
    - Feasibility.
    - Implementation constraints.
    - Rough cost and schedule ranges.

- **Finance/Budget Representative**
  - Provides guidance on:
    - Funding envelope.
    - Budget constraints and cycles.

- **Configuration / Document Controller**
  - Ensures ProgrammeRecord and associated documentation:
    - Are created and maintained under configuration control.
    - Are linked to baselines and decisions.

## 5. Inputs

The following inputs are required for programme governance activities:

1. **Strategic and policy frame**
   - `ERAGS-DOC-STR-001` (strategy).
   - `ERAGS-DOC-POL-001` (policy).
   - Context document (`ERAGS-DOC-CTX-001`) where needed.

2. **Performance and risk evidence**
   - PerformanceSummary (availability, MTTR, SLA).
   - KPIRecord with targets and thresholds (ERAGS-MOD-KPI-001 to -003).
   - IncidentSummary (safety and operational incidents).
   - EnergyCostSummary (energy and cost intensities).

3. **ProgrammeInitiationRecord / DecisionLogEntry**
   - Originating decision or trigger from:
     - Strategy and governance review (ERAGS-PROC-001).
     - Incident-driven intervention (ERAGS-PROC-008).
     - External directives.

4. **Existing ProgrammeRecord set**
   - Current approved programmes and their status.
   - Any programme risks or constraints.

5. **Indicative financial and resource constraints**
   - Funding envelope for planning period.
   - Major resource constraints (skills, access, procurement limits).

## 6. Pre-Conditions

Before evaluation or approval:

1. The System 1 Owner and Governance and Performance Analyst must:
   - Confirm that the performance/risk data used to justify programmes has passed basic QA checks (via PROC-007).
   - Document any known data limitations.

2. The Programme/Project Management Representative must:
   - Provide a rough feasibility assessment for each proposal (technical feasibility, high-level cost and delivery risk).

3. The Finance/Budget Representative must:
   - Provide current constraints and any relevant assumptions (for example expected budget for the next financial year).

4. The Configuration / Document Controller must:
   - Confirm the latest approved versions of relevant strategy and policy documents.
   - Ensure a ProgrammeRecord structure exists (as per ERAGS-MOD-DATA-001 and -002) to record proposals and decisions.

## 7. Procedure

### 7.1 Step 1 – Capture Programme Need and Initiation

1. The System 1 Owner creates or updates a **ProgrammeInitiationRecord** containing:
   - Link to originating DecisionLogEntry.
   - Problem statement (performance gap, risk, regulatory requirement).
   - High-level objective and expected outcomes.
   - Relevant KPIs and targets.
   - Preliminary scope indication (for example corridors or asset classes).

2. A draft **ProgrammeRecord** entry is created with:
   - ProgrammeID (unique).
   - Name and short description.
   - ProgrammeCategory (for example energy efficiency, resilience, safety, compliance).
   - Link to ProgrammeInitiationRecord and DecisionLogEntry.

### 7.2 Step 2 – Develop Programme Concept

The System 1 Owner, supported by technical and analytical roles, refines the concept into a **Programme Concept Note**, including:

1. Context and rationale:
   - Performance and KPI evidence.
   - Incidents and risks.
   - Policy/strategy alignment (explicit references to ERAGS-DOC-STR-001 goals and relevant policy clauses).

2. High-level technical scope:
   - Asset types and locations (for example number of luminaires, controllers, cabinets).
   - Key technologies (for example LED types, smart controllers, cabling upgrades).

3. Expected benefits:
   - Improvements in KPIs (availability, MTTR, energy intensity, safety).
   - Risk reductions (incident probabilities, severity).
   - Qualitative benefits (visibility, stakeholder satisfaction).

4. Rough order-of-magnitude (ROM) estimates:
   - Cost range (e.g. ±30% level).
   - Timeframe (start year, duration).---
DocID: ERAGS-PROC-002
Title: Programme Governance SOP
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
  - ERAGS-MOD-PROC-003
  - ERAGS-MOD-ARCH-001
  - ERAGS-MOD-ARCH-002
  - ERAGS-MOD-ARCH-003
  - ERAGS-MOD-DATA-001
  - ERAGS-MOD-DATA-002
  - ERAGS-MOD-FLOW-001
  - ERAGS-MOD-FLOW-002
  - ERAGS-MOD-KPI-001
  - ERAGS-MOD-KPI-002
  - ERAGS-MOD-KPI-003
RelatedDocs:
  - ERAGS-DOC-CTX-001
  - ERAGS-DOC-POL-001
  - ERAGS-DOC-STR-001
  - ERAGS-DOC-PROC-OV-001
  - ERAGS-DOC-STK-001
RelatedDataEntities:
  - ProgrammeRecord
  - Asset
  - PerformanceSummary
  - KPIRecord
  - IncidentSummary
  - EnergyCostSummary
  - DecisionLogEntry
  - GovernanceDocumentMetadata
ImplementsRequirements:
  - ERAGS-F-002
  - ERAGS-F-003
  - ERAGS-F-006
  - ERAGS-D-001
  - ERAGS-D-002
  - ERAGS-NF-002
  - ERAGS-NF-006
  - ERAGS-R-003
Alias:
  - PROC-Programme-Governance
---

# Programme Governance SOP  
*(ERAGS-PROC-002 / “PROC-Programme-Governance”)*

## 1. Purpose

This Standard Operating Procedure defines how investment and renewal **programmes** for electrical roads assets (artificial road lights, traffic signals and associated facilities) are:

- Identified and justified.
- Evaluated and prioritised.
- Approved and baselined.
- Monitored at the governance level.

The process ensures that programmes:

- Are grounded in strategy, performance gaps, risk, and regulatory requirements.
- Are aligned with available resources and constraints.
- Are traceable to decisions and evidence (data and analysis).

## 2. Scope

This process applies to all System 1 – ERAGS governance-level programmes that:

- Affect artificial road lights, traffic signals and associated facilities nationally or within defined areas/corridors.
- Require significant capital or operational expenditure and multi-year planning.
- Are governed at the level of the Director – Roads Network Maintenance and associated governance bodies.

Examples:

- LED retrofit programmes for specific corridors or regions.
- Traffic signal upgrade and standardisation programmes.
- Theft/vandalism mitigation programmes (for example cabling and cabinet protections).
- Smart control/telemetry rollout programmes.

Out of scope:

- Single, small maintenance actions or minor projects that do not constitute a formal programme (these are handled via operational work management systems).

## 3. Triggers

Programme Governance is initiated when:

1. **Strategic or governance review decisions**
   - From ERAGS-PROC-001, decisions such as:
     - “Initiate LED retrofit in high-energy-intensity corridors.”
     - “Develop a vandalism mitigation programme in high-incident areas.”

2. **Performance and KPI deviations**
   - Persistent KPI deviations beyond thresholds (ERAGS-MOD-KPI-003), indicating:
     - Structural shortcomings (for example ageing infrastructure, obsolete technology).
     - Need for targeted capital interventions.

3. **Regulatory or policy changes**
   - New requirements that demand systematic upgrades (for example new lighting standards).

4. **External funding opportunities**
   - Grants or budget allocations earmarked for specific interventions.

Each potential programme starts with a **ProgrammeInitiationRecord** linked to a DecisionLogEntry.

## 4. Roles and Responsibilities

(Aligned with ERAGS-DOC-STK-001.)

- **Director – Roads Network Maintenance**
  - Accountable for the programme portfolio.
  - Approves programme proposals and prioritisation.
  - Decides on funding allocation at the governance level.

- **Electrical Engineer – Roads Electrical Sub-Section (System 1 Owner)**
  - Owns the Programme Governance process within ERAGS.
  - Coordinates development and evaluation of programme proposals.
  - Ensures alignment with data-driven evidence and strategy.

- **Governance and Performance Analyst**
  - Provides analytical input:
    - Performance gaps.
    - KPI trends.
    - Risk and energy profiles.
  - Assists with defining benefits and expected impact.

- **Programme/Project Management Representative**
  - Advises on:
    - Feasibility.
    - Implementation constraints.
    - Rough cost and schedule ranges.

- **Finance/Budget Representative**
  - Provides guidance on:
    - Funding envelope.
    - Budget constraints and cycles.

- **Configuration / Document Controller**
  - Ensures ProgrammeRecord and associated documentation:
    - Are created and maintained under configuration control.
    - Are linked to baselines and decisions.

## 5. Inputs

The following inputs are required for programme governance activities:

1. **Strategic and policy frame**
   - `ERAGS-DOC-STR-001` (strategy).
   - `ERAGS-DOC-POL-001` (policy).
   - Context document (`ERAGS-DOC-CTX-001`) where needed.

2. **Performance and risk evidence**
   - PerformanceSummary (availability, MTTR, SLA).
   - KPIRecord with targets and thresholds (ERAGS-MOD-KPI-001 to -003).
   - IncidentSummary (safety and operational incidents).
   - EnergyCostSummary (energy and cost intensities).

3. **ProgrammeInitiationRecord / DecisionLogEntry**
   - Originating decision or trigger from:
     - Strategy and governance review (ERAGS-PROC-001).
     - Incident-driven intervention (ERAGS-PROC-008).
     - External directives.

4. **Existing ProgrammeRecord set**
   - Current approved programmes and their status.
   - Any programme risks or constraints.

5. **Indicative financial and resource constraints**
   - Funding envelope for planning period.
   - Major resource constraints (skills, access, procurement limits).

## 6. Pre-Conditions

Before evaluation or approval:

1. The System 1 Owner and Governance and Performance Analyst must:
   - Confirm that the performance/risk data used to justify programmes has passed basic QA checks (via PROC-007).
   - Document any known data limitations.

2. The Programme/Project Management Representative must:
   - Provide a rough feasibility assessment for each proposal (technical feasibility, high-level cost and delivery risk).

3. The Finance/Budget Representative must:
   - Provide current constraints and any relevant assumptions (for example expected budget for the next financial year).

4. The Configuration / Document Controller must:
   - Confirm the latest approved versions of relevant strategy and policy documents.
   - Ensure a ProgrammeRecord structure exists (as per ERAGS-MOD-DATA-001 and -002) to record proposals and decisions.

## 7. Procedure

### 7.1 Step 1 – Capture Programme Need and Initiation

1. The System 1 Owner creates or updates a **ProgrammeInitiationRecord** containing:
   - Link to originating DecisionLogEntry.
   - Problem statement (performance gap, risk, regulatory requirement).
   - High-level objective and expected outcomes.
   - Relevant KPIs and targets.
   - Preliminary scope indication (for example corridors or asset classes).

2. A draft **ProgrammeRecord** entry is created with:
   - ProgrammeID (unique).
   - Name and short description.
   - ProgrammeCategory (for example energy efficiency, resilience, safety, compliance).
   - Link to ProgrammeInitiationRecord and DecisionLogEntry.

### 7.2 Step 2 – Develop Programme Concept

The System 1 Owner, supported by technical and analytical roles, refines the concept into a **Programme Concept Note**, including:

1. Context and rationale:
   - Performance and KPI evidence.
   - Incidents and risks.
   - Policy/strategy alignment (explicit references to ERAGS-DOC-STR-001 goals and relevant policy clauses).

2. High-level technical scope:
   - Asset types and locations (for example number of luminaires, controllers, cabinets).
   - Key technologies (for example LED types, smart controllers, cabling upgrades).

3. Expected benefits:
   - Improvements in KPIs (availability, MTTR, energy intensity, safety).
   - Risk reductions (incident probabilities, severity).
   - Qualitative benefits (visibility, stakeholder satisfaction).

4. Rough order-of-magnitude (ROM) estimates:
   - Cost range (e.g. ±30% level).
   - Timeframe (start year, duration).

5. Dependencies and constraints:
   - Dependencies on other programmes or projects.
   - Known external constraints (for example road works schedules, regulatory approvals).

The Programme Concept Note is stored and linked to the ProgrammeRecord.

### 7.3 Step 3 – Evaluate and Prioritise Programme Proposals

When several programme proposals are under consideration:

1. The Governance and Performance Analyst prepares a **Programme Evaluation Pack**, including:
   - For each proposal:
     - Summary of rationale, benefits and ROM cost.
     - Expected KPI impact (if estimated).
     - Risk and criticality context (for example which corridors, safety implications).

2. Evaluation criteria are applied (according to strategy and policy), which may include:
   - Alignment with strategic objectives.
   - Magnitude and urgency of performance and risk issues addressed.
   - Cost-effectiveness (benefit vs cost).
   - Implementation feasibility.
   - Regulatory/compliance urgency.

3. A simple scoring or ranking is carried out, documented explicitly so it can be audited.

4. A **Programme Prioritisation Proposal** is prepared:
   - Suggested priority order.
   - Proposed phasing across years.
   - Identification of programmes that should be deferred or re-scoped.

### 7.4 Step 4 – Governance Review and Approval

1. The Programme Prioritisation Proposal is tabled in a governance forum (may be part of, or separate from, the Strategy and Governance Review session).

2. Participants include at least:
   - Director – Roads Network Maintenance.
   - System 1 Owner.
   - Governance and Performance Analyst.
   - Programme/Project Management Representative.
   - Finance/Budget Representative.

3. The forum reviews:
   - Alignment with strategy and policy.
   - Evidence base for each programme.
   - Affordability and timing.

4. For each programme, the forum decides to:
   - Approve (in full or partial).
   - Request further information/refinement.
   - Defer or reject.

5. Decisions are recorded as **DecisionLogEntry** items that reference:
   - ProgrammeID.
   - ProgrammeRecord.
   - ProgrammeEvaluation documentation.
   - Any conditions (for example “subject to detailed design and business case”).

### 7.5 Step 5 – Baseline Approved Programmes

For programmes that are **approved**:

1. ProgrammeRecord fields are updated to reflect:
   - Status = Approved.
   - TargetStartYear and indicative schedule.
   - Approved scope description at governance level.
   - DecisionLogEntry link.

2. The Configuration / Document Controller:
   - Updates or creates a relevant **baseline** (see ERAGS-MOD-CONF-001) if the updated programme portfolio represents a significant governance reference state.
   - Ensures that the baseline is:
     - Described in a baseline document (to be created later).
     - Tagged in Git where applicable.

3. If the programme requires detailed business case or design work:
   - This is recorded as a follow-up action and may initiate further processes outside System 1 (for example project-level design SOPs).

### 7.6 Step 6 – Communicate Programme Portfolio

The System 1 Owner prepares a **Programme Portfolio Summary** that:

- Lists all approved programmes, with:
  - Objectives.
  - High-level scope.
  - Timeframes.
  - Expected benefits.
- Summarises how the portfolio addresses:
  - Performance and KPI gaps.
  - Major risks and incidents.
  - Strategic and policy objectives.

This summary is shared with:

- Relevant operational teams and regional managers.
- Finance/Budget structures.
- Other governance forums as required.

### 7.7 Step 7 – Monitor Programmes at Governance Level

As programmes progress:

1. Programme/Project Management Representative provides updates on:
   - Schedule and milestones.
   - Cost performance (where available).
   - Major risks and issues.

2. The Governance and Performance Analyst:
   - Monitors **KPI and performance trends** in areas affected by programmes.
   - Provides periodic feedback on whether expected benefits are materialising.

3. The System 1 Owner:
   - Flags programmes requiring governance attention (major delays, cost overruns, under-delivery of benefits).
   - Initiates governance interventions if required (for example re-scoping, re-prioritisation).

4. Significant programme changes are fed back into:
   - `ERAGS-PROC-005_Change_Control_SOP.md` for controlled change.
   - `ERAGS-PROC-001_Strategy_and_Governance_Review_Process.md` for consideration at the next review cycle.

## 8. Outputs and Records

Key outputs of this process include:

1. **ProgrammeInitiationRecord**
   - Trigger and rationale for each programme concept.

2. **Programme Concept Note**
   - Rationale, scope, benefits, ROM cost and schedule.

3. **Programme Evaluation Pack**
   - Criteria, scores and prioritisation analysis.

4. **Programme Prioritisation Proposal**
   - Recommended portfolio and phasing.

5. **DecisionLogEntry records**
   - Approval, rejection or deferral decisions for each programme.

6. **ProgrammeRecord entries**
   - Formal records of approved programmes and their governance attributes.

7. **Programme Portfolio Summary**
   - Communicated view of the approved programme set.

These records support both day-to-day governance and external audit.

## 9. Interfaces with Other Processes

This SOP interfaces with:

- **ERAGS-PROC-001_Strategy_and_Governance_Review_Process**
  - Provides triggers and context for programmes.
  - Receives feedback on portfolio adequacy.

- **ERAGS-PROC-003_Performance_and_KPI_Review_SOP**
  - Supplies performance evidence for programme initiation.
  - Receives updates on performance impacts of programmes.

- **ERAGS-PROC-004_Policy_Management_SOP**
  - Some programmes may be triggered by policy changes or may require policy updates.

- **ERAGS-PROC-005_Change_Control_SOP**
  - Major changes to approved programmes are handled via change control.

- **ERAGS-PROC-006_Document_Lifecycle_and_Baseline_Management_SOP**
  - Programme-related baselines are created or updated here.

- **ERAGS-PROC-007_Data_Integration_and_Quality_Checks_SOP**
  - Ensures that performance, incident and energy data used in justification is of adequate quality.

- **ERAGS-PROC-008_Incident_Driven_Governance_Intervention_SOP**
  - Some programmes may be initiated specifically in response to serious incidents.

## 10. Metrics and Effectiveness Checks

Effectiveness of Programme Governance can be assessed via:

1. **Portfolio alignment**
   - Degree to which the portfolio covers:
     - Major performance gaps.
     - Key risk areas.
     - Strategic priorities.

2. **Decision traceability**
   - Ability to trace from an approved programme back to:
     - Originating KPI and incident evidence.
     - Strategic objectives.
     - DecisionLogEntry and evaluation records.

3. **Delivery performance (at governance level)**
   - Percentage of programmes starting on time.
   - Percentage of programmes significantly delayed or cancelled for governance reasons.

4. **Benefit realisation (high-level)**
   - Trends in performance KPIs in areas where programmes have been implemented.

These checks can later be formalised into QA checklists under `/qa`.

## 11. Compliance and Audit Considerations

Auditors should be able to:

- List all programmes approved in a given period from ProgrammeRecord.
- For sampled programmes:
  - Retrieve the ProgrammeInitiationRecord and Concept Note.
  - See evidence in PerformanceSummary, KPIRecord, IncidentSummary and EnergyCostSummary.
  - Review the Programme Evaluation Pack and Prioritisation Proposal.
  - Confirm existence of corresponding DecisionLogEntry items.
  - Confirm that baselines and document states have been managed via configuration processes.

This completes the definition of ERAGS-PROC-002 Programme Governance SOP.


5. Dependencies and constraints:
   - Dependencies on other programmes or projects.
   - Known external constraints (for example road works schedules, regulatory approvals).

The Programme Concept Note is stored and linked to the ProgrammeRecord.

### 7.3 Step 3 – Evaluate and Prioritise Programme Pro
