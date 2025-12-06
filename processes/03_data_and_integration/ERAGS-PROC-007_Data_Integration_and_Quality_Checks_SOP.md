---
DocID: ERAGS-PROC-007
Title: Data Integration and Quality Checks SOP
Version: 0.1
Status: Draft
OwnerRole: Electrical Engineer – Roads Electrical Sub-Section (System 1 Owner)
OwnerName: Fani Masoabi
ApproverRole: Director – Roads Network Maintenance
ApproverName: (to be designated)
CreatedDate: 2025-12-05
LastUpdatedDate: 2025-12-05
System: ERAGS (Electrical Roads Asset Governance & Strategy System)
ProcessFamily: DataAndIntegration
RelatedModels:
  - ERAGS-MOD-DATA-001_Governance_Data_Dictionary.md
  - ERAGS-MOD-DATA-002_Entity_Relationship_Model.md
  - ERAGS-MOD-DATA-003_Document_Metadata_Model.md
  - ERAGS-MOD-FLOW-001_External_Information_Flows.md
  - ERAGS-MOD-FLOW-002_Internal_ERAGS_Information_Flows.md
  - ERAGS-MOD-KPI-001_KPI_Definitions_and_Structure.md
  - ERAGS-MOD-KPI-002_KPI_Calculation_and_Data_Lineage_Model.md
RelatedDocs:
  - ERAGS-DOC-CTX-001
  - ERAGS-DOC-POL-001
  - ERAGS-DOC-STR-001
  - ERAGS-DOC-PROC-OV-001
  - ERAGS-DOC-OV-000
RelatedDataEntities:
  - Asset
  - KPIRecord
  - PerformanceSummary
  - IncidentSummary
  - EnergyCostSummary
  - ProgrammeRecord
  - GovernanceDocumentMetadata
  - DataQualityIssue
  - IntegrationRun
ImplementsRequirements:
  - ERAGS-D-001
  - ERAGS-D-002
  - ERAGS-D-003
  - ERAGS-D-004
  - ERAGS-NF-001
  - ERAGS-NF-002
  - ERAGS-NF-006
  - ERAGS-R-001
---

# Data Integration and Quality Checks SOP  
*(ERAGS-PROC-007)*

## 1. Purpose

This Standard Operating Procedure defines how System 1 – ERAGS:

- Integrates data from external operational systems into ERAGS governance data entities.
- Performs **data quality checks** to ensure that governance decisions are based on reliable information.
- Documents data quality issues and limitations, so they are visible to governance and audit.

The focus is on data required to support:

- KPI and performance reviews.
- Strategy and governance reviews.
- Programme governance.
- Policy management and compliance evidence.

## 2. Scope

This SOP covers:

- Integration of data from external systems into ERAGS-level entities, including:
  - Asset inventories (for example lighting poles, traffic signal installations).
  - Fault, work and incident data.
  - Energy and cost data.
  - Programme status summaries (where sourced from external project systems).
- Data quality checks applied at the governance layer, not every low-level operational validation.

External systems may include:

- Computerised Maintenance Management System (CMMS) or Work Management System (WMS).
- Geographic Information System (GIS).
- Traffic Management and Signal Control Systems.
- Utility billing systems (for example electricity billing).
- Project/Programme management tools.

The SOP is technology-agnostic; it assumes these systems exist and describes how ERAGS consumes and checks their data conceptually.

## 3. Roles and Responsibilities

- **Electrical Engineer – Roads Electrical Sub-Section (System 1 Owner)**
  - Owns the Data Integration and Quality Checks process.
  - Ensures that integrated data is sufficient and fit for governance purposes.
  - Decides how data quality limitations should be reported to governance.

- **Data Integration Specialist / CMMS-GIS Interface Role**
  - Operates and maintains the data integration pipelines (manual or automated).
  - Executes IntegrationRun procedures and initial checks.
  - Applies corrections where feasible and within mandate.

- **Governance and Performance Analyst**
  - Uses integrated data to create KPIRecord, PerformanceSummary, IncidentSummary and EnergyCostSummary.
  - Performs higher-level data quality analysis and documents limitations and impacts.

- **Configuration / Document Controller**
  - Ensures that data models, dictionaries and metadata conventions are up to date.
  - Tracks data-related configuration items in line with ERAGS-MOD-CONF models.

- **HSE Representative**
  - Provides input on classification and interpretation of safety-related incident data.

## 4. Inputs

1. **Data models and definitions**
   - ERAGS governance data dictionary (`ERAGS-MOD-DATA-001`).
   - Entity Relationship model (`ERAGS-MOD-DATA-002`).
   - Document metadata model (`ERAGS-MOD-DATA-003`).
   - KPI definitions and calculation/lineage models (`ERAGS-MOD-KPI-001` and `ERAGS-MOD-KPI-002`).

2. **External system data exports or feeds**
   - Asset registers and GIS datasets.
   - Fault and work order data from CMMS/WMS.
   - Incident logs (safety and operational).
   - Energy and billing data from utilities.
   - Programme or project status summaries (if used for ProgrammeRecord).

3. **Previous IntegrationRun records and DataQualityIssue logs**
   - For trend and history of data issues.

4. **Configuration metadata**
   - Mappings between external system fields and ERAGS entities (could be captured in a configuration document or model referenced from here).

## 5. Pre-Conditions

Before running an IntegrationRun for a given period:

1. The System 1 Owner and Data Integration Specialist must confirm:

   - Which external systems and data domains are in scope for the run.
   - The time window covered (for example monthly period, quarter, year).

2. The Configuration / Document Controller must verify that:

   - Relevant data models and mappings are **Approved** in their latest version.
   - Any planned changes to data structures are known and documented.

3. The Governance and Performance Analyst must indicate:

   - Which KPIs and governance processes will depend on this IntegrationRun, so that data quality focus can be prioritised accordingly.

## 6. Procedure – IntegrationRun

### 6.1 Step 1 – Initiate IntegrationRun

1. The Data Integration Specialist (or System 1 Owner in a small setup) creates an **IntegrationRun** record with:

   - IntegrationRunID (unique).
   - Date and time.
   - Period covered (for example 2025-10-01 to 2025-10-31).
   - Systems and data domains included (for example CMMS faults, GIS assets, utility billing).
   - Purpose (for example monthly KPI review, quarterly governance review).

2. The IntegrationRun record is stored in a suitable location (for example within a `/qa/data_quality/` folder or an internal log).

### 6.2 Step 2 – Extract/Receive External Data

For each external system:

1. Retrieve data for the defined period and scope:

   - Via export files (for example CSV, Excel, JSON).
   - Or via interfaces/APIs where available.

2. Store the raw extracts in a controlled location (for example an `/external_data/` directory outside the core ERAGS repo, referenced but not necessarily version-controlled if not appropriate).

3. Record in IntegrationRun:

   - File names, locations, or interface details.
   - Extract time.
   - Any filters or parameters used.

### 6.3 Step 3 – Transform and Map to ERAGS Entities

Using the data dictionary and ER models:

1. Map external fields to ERAGS entities and attributes (for example CMMS “work_order_id” to an internal “WorkOrderID”).

2. Apply necessary transformations, for example:

   - Unit conversions (for example hours to minutes).
   - Code or category mapping (for example failure codes to standardised incident categories).
   - Aggregations where required (for example summing energy use by area).

3. Create or update the following ERAGS entities as appropriate:

   - Asset (for example asset inventory snapshots).
   - IncidentSummary (from incident/fault logs).
   - PerformanceSummary (from work order and asset state data).
   - EnergyCostSummary (from billing).
   - ProgrammeRecord (where programme status is sourced from an external system).

4. Document key transformation rules and assumptions in IntegrationRun or a distinct **Data Integration Mapping Note** that is referenced by IntegrationRun.

### 6.4 Step 4 – Apply Data Quality Checks

The Data Integration Specialist and Governance and Performance Analyst perform data quality checks, which may include:

1. **Completeness checks**
   - Are all expected records for the period present?
   - For each domain, compare record counts with historical ranges.

2. **Consistency checks**
   - Cross-check totals and key metrics between domains, for example:
     - Number of faults vs number of incidents.
     - Energy use vs number of lights or historical values.
   - Check that:
     - Asset IDs referenced in fault/incident data exist in the Asset entity.

3. **Validity checks**
   - Check for invalid or out-of-range values, such as:
     - Negative durations or energy values.
     - Impossible dates (for example dates in the future for historical periods).

4. **Timeliness and freshness checks**
   - Confirm that data covers the intended period fully.
   - Identify delays or lags (for example incident records not captured until weeks later).

5. **Structural and mapping checks**
   - Confirm that field mappings have worked correctly.
   - Check that categorisations and codes align with expected values.

Any issues are logged as **DataQualityIssue** entries with:

- IssueID.
- Data domain.
- Severity (for example Low, Medium, High, Critical).
- Description.
- Impact assessment (on KPIs or governance decisions).
- Proposed mitigation (if any).

### 6.5 Step 5 – Decide on Fitness for Use

Based on the DataQualityIssue log:

1. The System 1 Owner, with the Governance and Performance Analyst, decides whether:

   - The integrated data is **fit for use** as-is for governance/KPI purposes.
   - It is fit for use if accompanied by clear caveats.
   - Certain aspects must be excluded from analysis due to poor quality.
   - A re-extraction or corrective data cleaning exercise is required before proceeding.

2. This decision and rationale are documented in an **IntegrationRun Summary Note**, which references:

   - IntegrationRunID.
   - Key data sources and transformations.
   - DataQualityIssue entries.
   - Overall fitness for use.

### 6.6 Step 6 – Provide Data to Downstream Processes

Once data is accepted (with or without caveats):

1. The Governance and Performance Analyst uses the integrated data to:

   - Compute KPIRecord for the period (per ERAGS-MOD-KPI-002).
   - Generate PerformanceSummary, IncidentSummary and EnergyCostSummary.

2. The IntegrationRun Summary Note and DataQualityIssue log are passed along as part of the input pack for:

   - Performance and KPI Review (ERAGS-PROC-003).
   - Strategy and Governance Review (ERAGS-PROC-001).
   - Programme Governance (ERAGS-PROC-002).
   - Policy Management (ERAGS-PROC-004).

3. Where significant data limitations exist, the Summary Note must explicitly flag them so they are visible and can be considered in governance decisions.

## 7. Outputs and Records

Key outputs and records of this SOP include:

1. **IntegrationRun record**
   - Unique ID, date, period, systems in scope, purpose.

2. **Raw extracts log**
   - References (not necessarily stored in the ERAGS repo) to external data files or API pulls.

3. **Transformed ERAGS entities**
   - Updated Asset, IncidentSummary, PerformanceSummary, EnergyCostSummary and related entities.

4. **DataQualityIssue log**
   - List of identified issues, severity, impact, and mitigation.

5. **Data Integration Mapping Note** (if used)
   - Documentation of field mappings and transformation rules.

6. **IntegrationRun Summary Note**
   - Overall assessment of fitness for use, with references to DataQualityIssue entries.

These records support both internal quality control and external audit.

## 8. Interfaces with Other Processes

This SOP interfaces with:

- **ERAGS-PROC-003_Performance_and_KPI_Review_SOP**
  - Provides the integrated datasets and data quality context for KPI and performance review.

- **ERAGS-PROC-001_Strategy_and_Governance_Review_Process**
  - Supplies underlying data and quality caveats for governance review.

- **ERAGS-PROC-002_Programme_Governance_SOP**
  - Supplies performance and risk evidence used in programme justification.

- **ERAGS-PROC-004_Policy_Management_SOP**
  - Supplies performance and incident evidence for policy changes.

- **ERAGS-PROC-005_Change_Control_SOP**
  - Changes to data models, mappings or integration rules follow change control.

- **ERAGS-PROC-006_Document_Lifecycle_and_Baseline_Management_SOP**
  - Data dictionaries, models and mapping documents are managed as configuration items.

- **ERAGS-PROC-008_Incident_Driven_Governance_Intervention_SOP**
  - High-severity incidents feed into IncidentSummary; data quality for those records is critical.

## 9. Metrics and Effectiveness Checks

Effectiveness of Data Integration and Quality Checks can be evaluated via:

1. **Data quality indicators**
   - Number and severity of DataQualityIssue entries per IntegrationRun.
   - Trends in recurring data quality problems.

2. **Coverage and completeness**
   - Proportion of planned data domains successfully integrated per period.
   - Incidence of missing data for key KPIs.

3. **Timeliness**
   - Time lag between period end and IntegrationRun completion.
   - Timeliness of data availability for governance reviews.

4. **Impact on decisions**
   - Number of governance decisions significantly constrained by data quality issues.

These can be formalised into QA checks and indicators under `/qa`.

## 10. Compliance and Audit Considerations

Auditors should be able to:

- Select a governance review period and find:
  - The corresponding IntegrationRun record(s).
  - Raw extract references.
  - DataQualityIssue logs.
  - IntegrationRun Summary Note.

- Confirm that:
  - Data used for KPI and governance decisions passed through this process.
  - Data quality limitations were recorded and communicated.
  - Changes to data models and integration rules were handled via change control and lifecycle/baseline management processes.

This completes the definition of ERAGS-PROC-007 Data Integration and Quality Checks SOP.
