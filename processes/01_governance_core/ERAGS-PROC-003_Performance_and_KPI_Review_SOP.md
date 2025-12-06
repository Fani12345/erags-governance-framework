---
DocID: ERAGS-PROC-003
Title: Performance and KPI Review SOP
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
  - ERAGS-MOD-KPI-001
  - ERAGS-MOD-KPI-002
  - ERAGS-MOD-KPI-003
  - ERAGS-MOD-DATA-001
  - ERAGS-MOD-DATA-002
  - ERAGS-MOD-FLOW-001
  - ERAGS-MOD-FLOW-002
  - ERAGS-MOD-ARCH-002
RelatedDocs:
  - ERAGS-DOC-CTX-001
  - ERAGS-DOC-POL-001
  - ERAGS-DOC-STR-001
  - ERAGS-DOC-PROC-OV-001
  - ERAGS-DOC-STK-001
RelatedDataEntities:
  - KPIRecord
  - PerformanceSummary
  - IncidentSummary
  - EnergyCostSummary
  - ProgrammeRecord
  - DecisionLogEntry
  - GovernanceDocumentMetadata
ImplementsRequirements:
  - ERAGS-F-008
  - ERAGS-F-003
  - ERAGS-D-002
  - ERAGS-D-003
  - ERAGS-NF-006
  - ERAGS-R-003
Alias:
  - PROC-Performance-Management
---

# Performance and KPI Review SOP  
*(ERAGS-PROC-003 / “PROC-Performance-Management”)*

## 1. Purpose

This Standard Operating Procedure defines how System 1 – ERAGS performs regular **Performance and Key Performance Indicator (KPI) reviews** for:

- Artificial road lighting.
- Traffic signals.
- Associated electrical and electronic facilities.

The process:

- Translates raw operational, incident and energy data into structured **KPIRecord** and **PerformanceSummary** entities.
- Applies KPI targets and threshold bands defined in the KPI models.
- Identifies deviations requiring governance attention.
- Provides structured inputs into:
  - Strategy and Governance Review (ERAGS-PROC-001).
  - Programme Governance (ERAGS-PROC-002).
  - Incident-driven interventions (ERAGS-PROC-008).

## 2. Scope

This SOP covers:

- Periodic performance reviews at System 1 level, typically:
  - Monthly or quarterly KPI review cycles.
- Asset classes:
  - Road lighting.
  - Traffic signals and related electronic control systems.
- Network scope:
  - National system or defined regions/areas, depending on how data is structured.

Out of scope:

- Real-time operational monitoring and dispatch.
- Detailed root-cause analyses at asset or project level (these may be triggered by this process, but are performed elsewhere).

## 3. Triggers

This process runs on a **regular schedule**, for example:

- Monthly KPI review.
- Quarterly in-depth performance review.

Additionally, ad hoc runs may be triggered when:

- Serious incidents occur.
- Major system failures are observed.
- Senior management requests an updated performance snapshot.

Each run is recorded as a **PerformanceReviewCycle** instance (can be a conceptual subset of DecisionLogEntry or a separate record type).

## 4. Roles and Responsibilities

(Aligned with ERAGS-DOC-STK-001.)

- **Electrical Engineer – Roads Electrical Sub-Section (System 1 Owner)**
  - Owns the performance and KPI review process.
  - Ensures data is available, quality checks are completed, and outputs are prepared.
  - Interprets results in the context of the electrical roads assets.

- **Governance and Performance Analyst**
  - Prepares KPIRecord, PerformanceSummary, IncidentSummary and EnergyCostSummary for the review period.
  - Performs trend and variance analyses.
  - Highlights significant deviations and patterns.

- **HSE Representative**
  - Provides interpretation of incidents (safety and operational).
  - Advises on incident-related KPIs and their implications.

- **Programme/Project Representative**
  - Provides context on ongoing programmes that may influence performance (for example new LED installations, major upgrades).

- **Configuration / Document Controller**
  - Ensures that KPI definitions, calculation rules and threshold bands are:
    - Up to date and Approved in the KPI models.
    - Under configuration control (via ERAGS-PROC-005 and ERAGS-PROC-006 where applicable).

## 5. Inputs

The following inputs are required for each Performance and KPI Review cycle:

1. **KPI definitions and rules**
   - KPI definitions and structure (`ERAGS-MOD-KPI-001`).
   - KPI calculation and data lineage model (`ERAGS-MOD-KPI-002`).
   - Governance decision rules and thresholds (`ERAGS-MOD-KPI-003`).

2. **Operational and incident data (via integrated datasets)**
   - Performance-related metrics:
     - Availability, MTTR, SLA compliance.
   - Incident data:
     - Incident counts, types, severity, locations.
   - Energy and cost data:
     - Energy_kWh, demand, costs.

3. **Aggregated entities**
   - KPIRecord set for the review period.
   - PerformanceSummary for the review period.
   - IncidentSummary and EnergyCostSummary for the review period.

4. **Programme context**
   - ProgrammeRecord information for:
     - Programmes affecting the areas/asset classes under review.

5. **Previous review outputs**
   - Previous KPI review findings.
   - Any actions or decisions taken as a result.

## 6. Pre-Conditions

Before running a performance and KPI review:

1. The System 1 Owner and Governance and Performance Analyst must confirm that:

   - Data for the review period has been integrated and validated via:
     - `ERAGS-PROC-007_Data_Integration_and_Quality_Checks_SOP.md`.
   - Any gaps or anomalies are documented and flagged in the review pack.

2. The KPI model artefacts must be in a consistent state:

   - Definitions, calculation rules and thresholds are:
     - Approved (Status = Approved in their metadata).
     - Not undergoing conflicting changes in the same review cycle.

3. A **Performance Review Calendar** is maintained, indicating:

   - Review period (for example 2025-10).
   - Planned review date.
   - Participants.

## 7. Procedure

### 7.1 Step 1 – Initiate Review Cycle

1. The System 1 Owner initiates a **PerformanceReviewCycle** record for the period, including:
   - Period start and end dates.
   - Assets / areas included.
   - Scheduled review meeting date.
   - Trigger type (scheduled or ad hoc).

2. Participants are notified and provided with the review date and scope.

### 7.2 Step 2 – Prepare KPI and Performance Datasets

The Governance and Performance Analyst:

1. Extracts or generates KPIRecord entries for the period:
   - Using the calculation rules in `ERAGS-MOD-KPI-002`.
   - Ensuring alignment with KPI definitions and IDs in `ERAGS-MOD-KPI-001`.

2. Produces:

   - **PerformanceSummary**:
     - Availability and MTTR by asset class and area.
     - SLA compliance measures.
   - **IncidentSummary**:
     - Incidents by type, severity, location, asset class.
   - **EnergyCostSummary**:
     - Energy_kWh and cost by asset class and area.

3. Validates the datasets:

   - Cross-checking totals where possible (for example energy totals against billing).
   - Ensuring that:
     - KPIRecord values are consistent with PerformanceSummary and underlying data.

4. Documents any limitations or data quality issues in a **Data Quality Note**.

### 7.3 Step 3 – Apply Targets and Thresholds

1. For each KPI:

   - Targets and threshold bands (Target, Warning, Intervention, Critical) are taken from `ERAGS-MOD-KPI-003`.

2. The Analyst:

   - Classifies each KPI value for the period into:
     - Within Target.
     - Warning.
     - Intervention.
     - Critical.
   - Computes basic trends:
     - Period-on-period changes.
     - Rolling averages where relevant.

3. A **KPI Status Table** is created, showing for each KPI and segment (for example corridor, region):

   - Current value.
   - Target.
   - Threshold band classification.
   - Short commentary (if required).

### 7.4 Step 4 – Identify Key Issues and Patterns

Using the KPI Status Table, PerformanceSummary, IncidentSummary and EnergyCostSummary, the Analyst and System 1 Owner jointly:

1. Identify **significant deviations**, such as:

   - KPIs in Critical or Intervention bands.
   - Persistent downward trends, even if still within Target.
   - Material increases in incident severity or frequency.

2. Group findings into **themes**, for example:

   - Ageing infrastructure in certain corridors.
   - High incident rates at specific intersections.
   - Energy hotspots where costs are rising.

3. For each theme, capture:

   - A short problem statement.
   - Associated KPIs and their trends.
   - Affected asset classes and locations.

These themes form the core of the narrative in the KPI review meeting.

### 7.5 Step 5 – Conduct KPI Review Session

Participants (as listed under Roles) meet to:

1. Review the **KPI and performance pack**, including:
   - KPI Status Table.
   - PerformanceSummary.
   - IncidentSummary.
   - EnergyCostSummary.
   - Data Quality Note (where necessary).

2. Discuss themes and underlying drivers:

   - Combine system-level data with local knowledge and operational feedback.
   - Consider the impact of ongoing programmes (ProgrammeRecord) on performance trends.

3. For each significant theme, determine:

   - Whether it can be managed operationally.
   - Whether it suggests a need for governance interventions:
     - Policy review (ERAGS-PROC-004).
     - Programme initiation or adjustment (ERAGS-PROC-002).
     - Strategy-level attention (ERAGS-PROC-001).
     - Incident-driven intervention (ERAGS-PROC-008).

4. Capture observations and candidate decisions as **KPIReviewNotes** (can be part of the meeting minutes or separate artefact).

### 7.6 Step 6 – Formulate Recommendations and Decisions

Following the discussion:

1. The System 1 Owner formulates, with the Analyst, a set of **recommendations**, which may include:

   - “Flag theme X for consideration in the next Strategy and Governance Review.”
   - “Propose a new LED retrofit programme in area Y.”
   - “Request a design or safety review of junction Z.”
   - “Review maintenance practices or response thresholds in region W.”

2. Where a decision is made at this level (for example to refer something directly to Change Control or Programme Governance), a **DecisionLogEntry** is created with:

   - Link to PerformanceReviewCycle.
   - KPIs involved.
   - Data and evidence used.
   - Follow-up process to be initiated.

3. If no immediate decisions are taken, the recommendations are carried forward as inputs into ERAGS-PROC-001 Strategy and Governance Review.

### 7.7 Step 7 – Document and Communicate Outcomes

1. The System 1 Owner prepares a **Performance and KPI Review Summary**, containing:

   - Period under review.
   - List of key KPI results.
   - Main themes and observations.
   - Recommendations and any decisions taken.
   - Reference to DecisionLogEntry records.

2. This summary is:

   - Shared with:
     - Governance structures.
     - Relevant operational teams and regional managers.
   - Filed under the appropriate repository location, with metadata.

## 8. Outputs and Records

Key outputs of this process are:

1. **PerformanceReviewCycle record**
   - Identification of each review run.

2. **KPIRecord set (period-specific)**
   - Calculated KPI values for the review period.

3. **PerformanceSummary, IncidentSummary, EnergyCostSummary**
   - Aggregated performance datasets.

4. **Data Quality Note**
   - Documentation of data quality issues and limitations.

5. **KPI Status Table and Analytical Pack**
   - Used in the review meeting.

6. **KPIReviewNotes / Meeting minutes**
   - Discussion points, themes, and considerations.

7. **Recommendations and DecisionLogEntry records**
   - Concrete outcomes and formalised decisions.

8. **Performance and KPI Review Summary**
   - Human-readable synthesis for governance and audit.

## 9. Interfaces with Other Processes

This SOP interfaces with:

- **ERAGS-PROC-007_Data_Integration_and_Quality_Checks_SOP**
  - Ensures data is integrated and validated before KPI calculation.

- **ERAGS-PROC-001_Strategy_and_Governance_Review_Process**
  - Receives synthesized KPI and performance information.
  - Provides structured inputs (themes and recommendations).

- **ERAGS-PROC-002_Programme_Governance_SOP**
  - Provides evidence for programme initiation and prioritisation.

- **ERAGS-PROC-004_Policy_Management_SOP**
  - May trigger policy review if systemic patterns emerge.

- **ERAGS-PROC-008_Incident_Driven_Governance_Intervention_SOP**
  - Provides incident-related KPI evidence that may require immediate interventions.

- **ERAGS-PROC-005 and ERAGS-PROC-006**
  - When KPI definitions, thresholds or calculation methods need to change.

## 10. Metrics and Effectiveness Checks

Effectiveness of this process can be assessed using:

1. **Completeness and timeliness**
   - Percentage of scheduled KPI reviews completed on time.
   - Coverage of all defined KPIs and relevant segments.

2. **Data quality**
   - Frequency and severity of data quality issues affecting KPI interpretation.
   - Trend in unresolved data gaps.

3. **Actionability**
   - Portion of KPI review cycles that result in:
     - Recommendations.
     - Decisions.
     - Initiation of downstream governance processes.

4. **Impact on performance**
   - Over time, trends in KPI results in areas where actions have been taken following reviews.

These can later be turned into concrete QA checks in `/qa`.

## 11. Compliance and Audit Considerations

Auditors should be able to:

- Identify each PerformanceReviewCycle in a given period.
- Retrieve:
  - KPIRecord, PerformanceSummary, IncidentSummary, EnergyCostSummary for that period.
  - KPI Status Table and analytical pack used.
  - KPIReviewNotes and the Performance and KPI Review Summary.
- Trace from:
  - KPI deviations → themes → recommendations → decisions (DecisionLogEntry).
  - Decisions → downstream processes (programme, policy, strategy, incident interventions).
- Confirm that:
  - KPI definitions, thresholds and calculation rules were stable or appropriately changed (with change control) during the review period.

This completes the definition of ERAGS-PROC-003 Performance and KPI Review SOP.
