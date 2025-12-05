---
DocID: ERAGS-MOD-DATA-001
Title: ERAGS Governance Data Dictionary
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
  - ERAGS-DOC-CTX-001
  - ERAGS-DOC-POL-001
  - ERAGS-DOC-STR-001
RelatedFolders:
  - requirements/
  - models/04_information_flows/
  - qa/
  - data/
---

# ERAGS Governance Data Dictionary

## 1. Purpose

This data dictionary defines the core data entities and attributes used by ERAGS at governance level. It implements and elaborates data requirements in ERAGS-REQ-HL-001 and ERAGS-REQ-DATA-001:

- ERAGS-D-001 – Governance Asset Data Definition  
- ERAGS-D-002 – Governance Performance Data Definition  
- ERAGS-D-003 – Data Quality Monitoring  
- ERAGS-D-004 – Document Metadata and Relationships

The focus is on **governance views** of data, not full operational databases of CMMS/GIS/Finance.

## 2. Entity Overview

Key governance entities:

- `AssetGovernanceRecord`
- `PerformanceSummary`
- `KPIRecord`
- `ProgrammeRecord`
- `DecisionLogEntry`
- `IncidentSummary`
- `EnergyCostSummary`
- `GovernanceDocumentMetadata`

Each entity below is described with:

- Field Name
- Description
- Data Type (conceptual)
- Allowed Values / Constraints
- Related Requirements

---

## 3. Entity: AssetGovernanceRecord

Represents a governance-relevant view of a physical asset (lighting point, signal, feeder, etc.).

| Field Name         | Description                                                       | Data Type | Allowed Values / Constraints                                        | Related Requirements       |
|--------------------|-------------------------------------------------------------------|----------|---------------------------------------------------------------------|----------------------------|
| AssetID            | Unique identifier for the asset (governance level).              | String    | Unique, stable ID; may map to CMMS/GIS native ID.                   | ERAGS-D-001, ERAGS-D-401   |
| AssetClass         | Broad class (e.g. StreetLight, TrafficSignal, FeederPillar).     | String    | Controlled list of classes.                                         | ERAGS-D-001, ERAGS-D-402   |
| SubClass           | More detailed subtype (e.g. LEDLuminaire, HPSLuminaire).         | String    | Controlled list per AssetClass.                                     | ERAGS-D-001                |
| LocationRef        | Reference to network location (road ID, chainage, etc.).         | String    | Should map to GIS / road referencing system.                        | ERAGS-D-001                |
| Latitude           | Latitude coordinate (if available at governance level).          | Number    | Valid geographic range.                                             | ERAGS-D-001, ERAGS-D-402   |
| Longitude          | Longitude coordinate.                                             | Number    | Valid geographic range.                                             | ERAGS-D-001, ERAGS-D-402   |
| AdministrativeArea | Area/district responsible for the asset.                         | String    | Controlled list of areas.                                           | ERAGS-D-001                |
| InstallYear        | Year of installation (or best estimate).                         | Integer   | Reasonable year range; may be null if unknown.                      | ERAGS-D-001, ERAGS-D-402   |
| ConditionRating    | Governance-level condition indicator.                            | String    | e.g. Good / Fair / Poor, or numeric 1–5 scale, defined elsewhere.   | ERAGS-D-001, ERAGS-D-402   |
| CriticalityClass   | Criticality level for governance decisions.                      | String    | e.g. Critical / High / Medium / Low, defined in policy/strategy.    | ERAGS-D-001                |
| OwnershipType      | Ownership of asset (e.g. PublicRoads, Municipality, Concession). | String    | Controlled list.                                                    | ERAGS-D-001                |
| Notes              | Free-text governance notes.                                      | String    | Optional.                                                           | ERAGS-D-001                |

---

## 4. Entity: PerformanceSummary

Represents aggregated performance metrics for a group of assets over a defined period.

| Field Name        | Description                                                       | Data Type | Allowed Values / Constraints                                   | Related Requirements            |
|-------------------|-------------------------------------------------------------------|----------|----------------------------------------------------------------|---------------------------------|
| PerfID            | Unique identifier for the performance summary record.             | String    | Unique per summarisation period and aggregation level.         | ERAGS-D-002, ERAGS-D-401        |
| PeriodStart       | Start date of the period.                                         | Date      | ISO date; PeriodStart ≤ PeriodEnd.                             | ERAGS-D-002, ERAGS-D-403        |
| PeriodEnd         | End date of the period.                                           | Date      | ISO date; PeriodEnd ≥ PeriodStart.                             | ERAGS-D-002, ERAGS-D-403        |
| AggregationLevel  | Level of aggregation (e.g. AssetClass, Corridor, Area).          | String    | Controlled list.                                               | ERAGS-D-002                     |
| AggregationKey    | Value for the chosen aggregation level (e.g. Corridor ID).       | String    | Must be compatible with AssetGovernanceRecord attributes.      | ERAGS-D-002                     |
| AvailabilityPct   | Availability percentage for the period.                           | Number    | 0–100; derived from fault/uptime data.                         | ERAGS-D-002, ERAGS-D-402        |
| MeanTimeToRepairH | Mean time to repair in hours.                                     | Number    | ≥ 0; can be null if insufficient data.                         | ERAGS-D-002, ERAGS-D-402        |
| ResponseTimeCompliancePct | % of faults resolved within SLA.                          | Number    | 0–100.                                                         | ERAGS-D-002                     |
| FaultCount        | Number of faults in the period.                                   | Integer   | ≥ 0.                                                           | ERAGS-D-002                     |
| CustomerComplaints| Number of complaints related to this aggregation.                 | Integer   | ≥ 0.                                                           | ERAGS-D-002                     |
| SafetyIncidents   | Number of safety incidents related to this aggregation.           | Integer   | ≥ 0.                                                           | ERAGS-D-002, ERAGS-D-003        |

---

## 5. Entity: KPIRecord

Represents a specific KPI value for a period and scope.

| Field Name      | Description                                            | Data Type | Allowed Values / Constraints                           | Related Requirements         |
|-----------------|--------------------------------------------------------|----------|--------------------------------------------------------|------------------------------|
| KPIRecordID     | Unique identifier.                                     | String    | Unique.                                                | ERAGS-D-002                  |
| KPINamedID      | Logical KPI identifier (e.g. LightingAvailability).   | String    | Controlled list; defined in KPI model.                 | ERAGS-D-002                  |
| PeriodStart     | Start date of KPI period.                              | Date      |                                                        | ERAGS-D-002, ERAGS-D-403     |
| PeriodEnd       | End date of KPI period.                                | Date      |                                                        | ERAGS-D-002, ERAGS-D-403     |
| ScopeType       | Scope type (SystemWide, Area, Corridor, AssetClass).  | String    | Controlled list.                                       | ERAGS-D-002                  |
| ScopeKey        | Scope identifier (e.g. area code, corridor ID).       | String    |                                                        | ERAGS-D-002                  |
| KPIValue        | Numeric KPI value.                                     | Number    |                                                        | ERAGS-D-002                  |
| TargetValue     | Target value defined by ERAGS.                         | Number    |                                                        | ERAGS-D-002, ERAGS-F-008     |
| ThresholdFlags  | Encoded flags (e.g. AboveTarget, BelowWarningLevel).  | String    | Defined code list.                                     | ERAGS-D-002, ERAGS-NF-006    |
| SourcePerfID    | Link to underlying PerformanceSummary where relevant. | String    | Foreign key to PerfID (if applicable).                 | ERAGS-D-002, ERAGS-D-003     |

---

## 6. Entity: ProgrammeRecord

Represents a candidate or approved programme element (group of projects or interventions).

| Field Name        | Description                                          | Data Type | Allowed Values / Constraints                       | Related Requirements         |
|-------------------|------------------------------------------------------|----------|----------------------------------------------------|------------------------------|
| ProgrammeID       | Unique identifier for the programme item.           | String    | Unique.                                            | ERAGS-F-006, ERAGS-D-001     |
| ProgrammeName     | Short descriptive name.                             | String    |                                                    | ERAGS-F-006                  |
| ProgrammeType     | Type (Renewal, Upgrade, NewInstall, Pilot, etc.).   | String    | Controlled list.                                   | ERAGS-F-006                  |
| TimeHorizon       | Time horizon (Annual, MultiYear).                   | String    | Controlled list.                                   | ERAGS-F-006                  |
| TargetStartYear   | Intended start year.                                | Integer   |                                                    | ERAGS-F-006                  |
| EstimatedCost     | Estimated total cost (governance level).            | Number    | Currency units as defined in finance conventions.  | ERAGS-D-002                  |
| PriorityRank      | Priority order among candidate programmes.          | Integer   | ≥ 1; relative ranking within cycle.                | ERAGS-F-006                  |
| PrimaryDrivers    | Key drivers (Safety, Reliability, Energy, etc.).    | String    | Multi-value (comma-separated controlled codes).     | ERAGS-F-006                  |
| Status            | Status (Proposed, UnderReview, Approved, Deferred). | String    | Controlled list.                                   | ERAGS-F-006, ERAGS-R-003     |

---

## 7. Entity: DecisionLogEntry

Represents a governance decision relevant to ERAGS.

| Field Name       | Description                                               | Data Type | Allowed Values / Constraints                          | Related Requirements        |
|------------------|-----------------------------------------------------------|----------|-------------------------------------------------------|-----------------------------|
| DecisionID       | Unique identifier for the decision record.                | String    | Unique.                                               | ERAGS-R-003                 |
| DecisionDate     | Date of decision.                                         | Date      |                                                       | ERAGS-R-003                 |
| DecisionType     | Type (Policy, Strategy, Programme, Standard, etc.).       | String    | Controlled list.                                      | ERAGS-R-003                 |
| DecisionSummary  | Concise description of the decision.                      | String    |                                                       | ERAGS-R-003                 |
| RelatedDocIDs    | IDs of related documents (policy, strategy, programme).   | String    | One or more DocIDs, separated by commas.              | ERAGS-R-003, ERAGS-D-004    |
| RelatedReqIDs    | IDs of related requirements (if applicable).              | String    | One or more Requirement_IDs, separated by commas.     | ERAGS-R-003, ERAGS-NF-002   |
| Rationale        | Summary of main rationale/reasons.                        | String    |                                                       | ERAGS-R-003                 |
| ApproverRole     | Role of approving authority.                              | String    | Controlled list of roles.                             | ERAGS-R-003                 |
| ApproverName     | Name of individual approver (optional).                   | String    |                                                       | ERAGS-R-003                 |

---

## 8. Entity: IncidentSummary

Summarised safety or incident data relevant to governance.

| Field Name        | Description                                             | Data Type | Allowed Values / Constraints                          | Related Requirements     |
|-------------------|---------------------------------------------------------|----------|-------------------------------------------------------|--------------------------|
| IncidentSumID     | Unique identifier.                                      | String    | Unique.                                               | ERAGS-D-002, ERAGS-D-003 |
| PeriodStart       | Start date of incident summary period.                  | Date      |                                                       | ERAGS-D-002, ERAGS-D-403 |
| PeriodEnd         | End date of incident summary period.                    | Date      |                                                       | ERAGS-D-002, ERAGS-D-403 |
| AggregationLevel  | Level (SystemWide, Area, Corridor).                     | String    | Controlled list.                                      | ERAGS-D-002              |
| AggregationKey    | Key value (e.g. area code).                             | String    |                                                       | ERAGS-D-002              |
| IncidentCount     | Count of incidents.                                     | Integer   | ≥ 0.                                                 | ERAGS-D-002              |
| SeverityIndex     | Aggregate severity index (optional).                    | Number    | Defined calculation method.                           | ERAGS-D-002              |
| RelatedAssetClass | Optional link to AssetClass (if specific).              | String    | Matches AssetGovernanceRecord.AssetClass where used. | ERAGS-D-001              |

---

## 9. Entity: EnergyCostSummary

Summarised energy and cost data for governance-level analysis.

| Field Name        | Description                                            | Data Type | Allowed Values / Constraints                         | Related Requirements     |
|-------------------|--------------------------------------------------------|----------|------------------------------------------------------|--------------------------|
| EnergyCostID      | Unique identifier.                                     | String    | Unique.                                              | ERAGS-D-002              |
| PeriodStart       | Start date of energy/cost period.                      | Date      |                                                      | ERAGS-D-002, ERAGS-D-403 |
| PeriodEnd         | End date of energy/cost period.                        | Date      |                                                      | ERAGS-D-002, ERAGS-D-403 |
| AggregationLevel  | Level (Feeder, Area, Corridor, SystemWide).           | String    | Controlled list.                                     | ERAGS-D-002              |
| AggregationKey    | Key value (e.g. feeder ID, area code).                | String    |                                                      | ERAGS-D-002              |
| Energy_kWh        | Total energy consumed.                                 | Number    | ≥ 0.                                                 | ERAGS-D-002              |
| Cost_Total        | Total cost over period.                                | Number    | ≥ 0.                                                 | ERAGS-D-002              |
| TariffCode        | Applicable tariff code (if tracked at this level).    | String    | Controlled list.                                     | ERAGS-D-002              |

---

## 10. Entity: GovernanceDocumentMetadata

Logical representation of document metadata fields used across `/docs` and `/requirements`.

| Field Name      | Description                                           | Data Type | Allowed Values / Constraints                       | Related Requirements     |
|-----------------|-------------------------------------------------------|----------|----------------------------------------------------|--------------------------|
| DocID           | Unique document identifier.                           | String    | Unique within ERAGS.                               | ERAGS-D-004              |
| Title           | Document title.                                       | String    |                                                    | ERAGS-D-004              |
| Version         | Version label (e.g. 0.1, 1.0).                         | String    | Simple semantic versioning recommended.            | ERAGS-D-004              |
| Status          | Status (Draft, UnderReview, Approved, Superseded).    | String    | Controlled list.                                   | ERAGS-D-004, ERAGS-R-003 |
| OwnerRole       | Role responsible for document.                        | String    |                                                    | ERAGS-D-004              |
| OwnerName       | Name of current owner (optional).                     | String    |                                                    | ERAGS-D-004              |
| ApproverRole    | Role authorised to approve.                           | String    |                                                    | ERAGS-D-004, ERAGS-R-003 |
| ApproverName    | Name of approver (optional).                          | String    |                                                    | ERAGS-D-004, ERAGS-R-003 |
| CreatedDate     | Creation date.                                        | Date      |                                                    | ERAGS-D-004              |
| LastUpdatedDate | Last updated date.                                    | Date      |                                                    | ERAGS-D-004              |
| System          | System this document belongs to (e.g. ERAGS).         | String    |                                                    | ERAGS-D-004              |
| RelatedDocs     | List of related DocIDs.                               | String    | Comma-separated DocIDs.                            | ERAGS-D-004              |
| RelatedFolders  | List of related folder paths.                          | String    | Comma-separated relative paths.                     | ERAGS-D-004              |

---

## 11. Relationship to Other Artefacts

- The **entity list and fields** here shall be used when creating:
  - Interface models (`models/04_information_flows/`).
  - KPI and decision models (`models/05_kpi_and_analytics_models/`).
  - QA checks for data completeness and consistency (`/qa`).
  - Example CSV files in `/data`.

- This document is an implementing artefact for:
  - ERAGS-D-001, ERAGS-D-002, ERAGS-D-004 and derived data requirements.
  - Relevant entries in `ERAGS_RTM.csv` should reference `models/03_data_models/ERAGS-MOD-DATA-001_Governance_Data_Dictionary.md`.
