---
DocID: ERAGS-MOD-KPI-002
Title: ERAGS KPI Calculation and Data Lineage Model
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
  - ERAGS-MOD-KPI-001
  - ERAGS-MOD-DATA-001
  - ERAGS-MOD-DATA-002
  - ERAGS-MOD-FLOW-001
  - ERAGS-MOD-FLOW-002
  - ERAGS-DOC-PROC-OV-001
RelatedFolders:
  - models/03_data_models/
  - models/04_information_flows/
  - qa/
---

# ERAGS KPI Calculation and Data Lineage Model

## 1. Purpose

This document describes:

- How KPIRecord values are calculated from underlying data entities.
- How data flows from external systems through ERAGS to KPI calculations.
- Data lineage for key KPIs (source → transformation → KPI).

It ensures transparency and reproducibility of KPIs, supporting:

- ERAGS-F-008 – Performance and KPI Management.
- ERAGS-D-002, ERAGS-D-003 – Performance data and data quality.
- ERAGS-NF-002, ERAGS-NF-006 – Traceability and governance of performance.

## 2. General Calculation Approach

1. External systems (CMMS/WFM, GIS, HSE, Finance) provide operational data.
2. Data & Information Integration Component:
   - Cleans, aggregates and maps data into governance entities:
     - PerformanceSummary
     - IncidentSummary
     - EnergyCostSummary
3. Analytics / KPI systems:
   - Use these governance entities to compute KPIRecord entries according to ERAGS-MOD-KPI-001.
4. Performance & KPI Management Component:
   - Validates KPIRecord values.
   - Stores and interprets them for governance processes.

---

## 3. Data Lineage Examples

### 3.1 Lighting Availability (KPI-AV-001)

**Source data:**

- CMMS fault and work order records.
- Possibly smart-control system logs (if available).

**Governance entities:**

- PerformanceSummary records with:
  - AvailabilityPct
  - FaultCount
  - AggregationLevel, AggregationKey
  - PeriodStart, PeriodEnd

**Lineage steps:**

1. CMMS/WFM aggregates operational data by:
   - AssetClass = StreetLight.
   - Geographic or organisational aggregation as required.
2. Data & Information Integration:
   - Validates counts and durations.
   - Forms PerformanceSummary entries per period and aggregation.
3. Analytics/KPI:
   - For each required scope and period, retrieves relevant PerformanceSummary entries.
   - Computes overall AvailabilityPct (if further aggregation needed).
4. KPIRecord:
   - Creates KPIRecord entries:
     - KPINamedID = KPI-AV-001
     - KPIValue = computed AvailabilityPct
     - PeriodStart/End = as per aggregation
     - ScopeType/ScopeKey = as defined
     - TargetValue and ThresholdFlags set according to ERAGS-MOD-KPI-003.

### 3.2 Traffic Signal Availability (KPI-AV-002)

Same pattern as KPI-AV-001 but with AssetClass = TrafficSignal.

### 3.3 Mean Time to Repair (KPI-RT-001)

**Source data:**

- CMMS/WFM: open/close times for faults.

**Lineage:**

1. CMMS calculates average time between fault detection and repair completion per period.
2. Data & Information Integration:
   - Ingests these aggregates as PerformanceSummary.MeanTimeToRepairH.
3. KPIRecord:
   - Uses those values directly or further aggregates if needed, storing them as KPIValue with KPINamedID = KPI-RT-001.

### 3.4 SLA Compliance (KPI-SL-001)

**Source data:**

- CMMS: time to attend/resolve faults, SLA rules.

**Lineage:**

1. CMMS computes percentage of faults resolved within defined SLA time windows.
2. Data & Information Integration:
   - Ingests PerformanceSummary.ResponseTimeCompliancePct.
3. KPIRecord:
   - Sets KPIValue from ResponseTimeCompliancePct for KPINamedID = KPI-SL-001.

### 3.5 Safety Incident Rate (KPI-SF-001)

**Source data:**

- HSE Incident system: incident records with classification, severity and location.

**Lineage:**

1. HSE system groups incidents into IncidentSummary by period and scope.
2. Data & Information Integration:
   - Aligns IncidentSummary with ERAGS aggregation scheme.
3. Analytics/KPI:
   - Obtains Exposure data (for example asset counts or traffic volumes from other systems).
   - Computes IncidentRate.
4. KPIRecord:
   - KPINamedID = KPI-SF-001; KPIValue = IncidentRate.

### 3.6 Energy Intensity (KPI-EN-001)

**Source data:**

- Finance/Energy: billing records, energy meter readings.
- AssetInventory: number of lighting points, lengths of lit roads.

**Lineage:**

1. Finance/Energy produces EnergyCostSummary (Energy_kWh, Cost_Total).
2. Data & Information Integration:
   - Aligns EnergyCostSummary with AssetGovernanceRecord populations.
3. Analytics/KPI:
   - Computes EnergyIntensity = Energy_kWh / NormalisationFactor.
4. KPIRecord:
   - KPINamedID = KPI-EN-001; KPIValue = EnergyIntensity.

---

## 4. Data Quality and Validation

For each KPI:

- Minimum data completeness thresholds must be met (for example ≥ x% of assets reporting, or minimum fault counts).
- Basic validation:
  - Check that periods and scopes match across PerformanceSummary, IncidentSummary and EnergyCostSummary.
  - Confirm that no impossible values occur (negative hours, percentages > 100, etc.).

These checks:

- Are defined in QA artefacts under `/qa`.
- Are informed by relationships in `ERAGS-MOD-DATA-002` and flows in `ERAGS-MOD-FLOW-001`/`002`.

---

## 5. Traceability

- Each KPIRecord should be traceable back to:
  - Source governance entities (PerformanceSummary, IncidentSummary, EnergyCostSummary).
  - Source systems providing raw data.
  - Calculation logic in this document and ERAGS-MOD-KPI-001.

This enables:

- Audit of KPI values.
- Recalculation if data or definitions change.
- Impact analysis when changing KPI definitions or data sources.

---

## 6. Relationship to Requirements and RTM

This model is an implementing artefact for:

- ERAGS-F-008, ERAGS-D-002, ERAGS-D-003.
- ERAGS-NF-002 and ERAGS-NF-006.

It should be referenced in `ERAGS_RTM.csv` under `Implementing_Document_or_Process` for those requirement IDs.
