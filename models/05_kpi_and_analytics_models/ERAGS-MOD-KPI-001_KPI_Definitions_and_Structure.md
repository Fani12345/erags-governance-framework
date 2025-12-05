---
DocID: ERAGS-MOD-KPI-001
Title: ERAGS KPI Definitions and Structure
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
  - ERAGS-DOC-POL-001
  - ERAGS-DOC-STR-001
  - ERAGS-DOC-PROC-OV-001
  - ERAGS-MOD-DATA-001
  - ERAGS-MOD-DATA-002
RelatedFolders:
  - models/03_data_models/
  - models/04_information_flows/
  - qa/
---

# ERAGS KPI Definitions and Structure

## 1. Purpose

This document defines the key governance Key Performance Indicators (KPIs) used by ERAGS for artificial road lights, traffic signals and associated facilities. It provides:

- Standard names and identifiers for KPIs.
- Conceptual definitions and calculation descriptions.
- Linkage to data entities defined in `ERAGS-MOD-DATA-001`.
- Alignment with policy and strategy goals.

It implements and elaborates requirements:

- ERAGS-F-008 – Performance and KPI Management.
- ERAGS-D-002 – Governance Performance Data Definition.
- ERAGS-NF-006 – Governance Performance Monitoring.

## 2. KPI Catalogue Structure

Each KPI is described using:

- KPI_ID – Stable identifier.
- Name – Human-readable name.
- Description – What the KPI measures.
- Formula – Conceptual calculation.
- Measurement_Period – Time window (e.g. monthly, yearly).
- Scope – Level at which KPI is reported (system, area, corridor, asset class).
- Data_Sources – Entities and fields used.
- Direction – Desired direction (higher is better / lower is better / target band).
- Targets_and_Thresholds – Reference to decision thresholds (defined in ERAGS-MOD-KPI-003).
- Related_Requirements – Key requirements that the KPI supports.

---

## 3. KPI Definitions

### 3.1 KPI-AV-001 – Lighting Availability

- **KPI_ID:** KPI-AV-001  
- **Name:** Lighting Availability  
- **Description:** Percentage of time that street-lighting points are available (not in fault) over the measurement period.  
- **Formula (conceptual):**  
  - `AvailabilityPct = 100 × (TotalAvailableTime / TotalPossibleTime)`  
  - Typically calculated from aggregated PerformanceSummary.AvailabilityPct for lighting asset classes.  
- **Measurement_Period:** Monthly; aggregated to yearly for strategic reviews.  
- **Scope:** System-wide, area, corridor, and optionally administrative area.  
- **Data_Sources:**
  - PerformanceSummary.AvailabilityPct where AssetClass = StreetLight.
- **Direction:** Higher is better.  
- **Targets_and_Thresholds:** See ERAGS-MOD-KPI-003 (minimum targets per scope).  
- **Related_Requirements:** ERAGS-F-002, ERAGS-F-006, ERAGS-F-008, ERAGS-D-002.

### 3.2 KPI-AV-002 – Traffic Signal Availability

- **KPI_ID:** KPI-AV-002  
- **Name:** Traffic Signal Availability  
- **Description:** Percentage of time that traffic signal installations are operational.  
- **Formula (conceptual):**  
  - Similar to KPI-AV-001, but for AssetClass = TrafficSignal.  
- **Measurement_Period:** Monthly; aggregated to yearly.  
- **Scope:** System-wide, area, corridor, strategic intersections.  
- **Data_Sources:**
  - PerformanceSummary.AvailabilityPct where AssetClass = TrafficSignal.
- **Direction:** Higher is better.  
- **Targets_and_Thresholds:** Defined per criticality (high-criticality junctions may have higher targets).  
- **Related_Requirements:** ERAGS-F-002, ERAGS-F-006, ERAGS-F-008, ERAGS-D-002.

### 3.3 KPI-RT-001 – Mean Time to Repair (MTTR)

- **KPI_ID:** KPI-RT-001  
- **Name:** Mean Time to Repair – Electrical Assets  
- **Description:** Average time taken to restore faulty lighting and signal assets.  
- **Formula (conceptual):**  
  - From PerformanceSummary.MeanTimeToRepairH for relevant aggregations.  
- **Measurement_Period:** Monthly.  
- **Scope:** Asset class, area, corridor.  
- **Data_Sources:**
  - PerformanceSummary.MeanTimeToRepairH.
- **Direction:** Lower is better.  
- **Targets_and_Thresholds:** Defined per asset class and criticality.  
- **Related_Requirements:** ERAGS-F-006, ERAGS-F-008, ERAGS-D-002.

### 3.4 KPI-SL-001 – SLA Compliance for Fault Response

- **KPI_ID:** KPI-SL-001  
- **Name:** SLA Compliance – Fault Response  
- **Description:** Percentage of faults resolved within agreed service-level response times.  
- **Formula (conceptual):**  
  - From PerformanceSummary.ResponseTimeCompliancePct.  
- **Measurement_Period:** Monthly.  
- **Scope:** System, area, corridor, contractor (if applicable).  
- **Data_Sources:**
  - PerformanceSummary.ResponseTimeCompliancePct.
- **Direction:** Higher is better.  
- **Targets_and_Thresholds:** See ERAGS-MOD-KPI-003.  
- **Related_Requirements:** ERAGS-F-006, ERAGS-F-008, ERAGS-D-002.

### 3.5 KPI-SF-001 – Safety Incident Rate

- **KPI_ID:** KPI-SF-001  
- **Name:** Safety Incident Rate – Electrical Roads Assets  
- **Description:** Rate of safety incidents involving electrical roads assets per unit of exposure (for example per million vehicle-kilometres, or per 1000 assets).  
- **Formula (conceptual):**  
  - `IncidentRate = IncidentCount / Exposure`  
  - Where IncidentCount from IncidentSummary; Exposure defined in policy/analytics.  
- **Measurement_Period:** Quarterly and yearly.  
- **Scope:** System, area, corridor.  
- **Data_Sources:**
  - IncidentSummary.IncidentCount, SeverityIndex (optional).  
- **Direction:** Lower is better.  
- **Targets_and_Thresholds:** Zero or near-zero targets for severe incidents; defined in risk policy.  
- **Related_Requirements:** ERAGS-F-002, ERAGS-F-008, ERAGS-D-002, ERAGS-D-003.

### 3.6 KPI-EN-001 – Energy Intensity of Lighting

- **KPI_ID:** KPI-EN-001  
- **Name:** Energy Intensity – Lighting  
- **Description:** Energy consumption per lighting point or per kilometre for street lighting.  
- **Formula (conceptual):**  
  - `EnergyIntensity = Energy_kWh / NormalisationFactor`  
  - NormalisationFactor may be number of points, length of lit road, or other quantity.  
- **Measurement_Period:** Monthly; aggregated to yearly.  
- **Scope:** System, area, corridor.  
- **Data_Sources:**
  - EnergyCostSummary.Energy_kWh; AssetGovernanceRecord counts.  
- **Direction:** Lower is better (for same or better service).  
- **Targets_and_Thresholds:** Linked to energy-efficiency objectives in strategy.  
- **Related_Requirements:** ERAGS-F-002, ERAGS-F-006, ERAGS-F-008, ERAGS-D-002.

### 3.7 KPI-VD-001 – Vandalism and Theft Rate

- **KPI_ID:** KPI-VD-001  
- **Name:** Vandalism and Theft Rate – Electrical Assets  
- **Description:** Number of vandalism/theft incidents affecting electrical roads assets per unit of exposure.  
- **Formula (conceptual):**  
  - `VandalismRate = IncidentCount / Exposure`  
  - Based on IncidentSummary records flagged as vandalism/theft.  
- **Measurement_Period:** Quarterly; tracked yearly.  
- **Scope:** System, area, corridor.  
- **Data_Sources:**
  - IncidentSummary.IncidentCount with vandalism classification.  
- **Direction:** Lower is better.  
- **Targets_and_Thresholds:** Defined in resilience/security policies.  
- **Related_Requirements:** ERAGS-F-002, ERAGS-F-006, ERAGS-F-008, ERAGS-D-002.

### 3.8 KPI-PR-001 – Programme Delivery Performance

- **KPI_ID:** KPI-PR-001  
- **Name:** Programme Delivery Performance  
- **Description:** Degree to which approved programmes are delivered on time and within budget.  
- **Formula (conceptual):**
  - Time performance: % of programme milestones achieved by planned dates.
  - Cost performance: % variance between planned and actual cost.  
- **Measurement_Period:** Annual.  
- **Scope:** System-wide; by programme type.  
- **Data_Sources:**
  - ProgrammeRecord.Status, TargetStartYear, milestone info (via external systems).
  - Finance data for cost.  
- **Direction:** Higher on-time % is better; lower cost variance is better.  
- **Targets_and_Thresholds:** Defined in strategy and programme governance.  
- **Related_Requirements:** ERAGS-F-006, ERAGS-F-008.

---

## 4. Governance of KPI Definitions

- KPI definitions shall be:
  - Approved through policy/strategy governance processes.
  - Version-controlled as part of ERAGS documentation.
- Changes to KPIs (definitions, formulas, targets) must:
  - Be captured as decisions (DecisionLogEntry).
  - Trigger review of related requirements and processes if needed.

---

## 5. Relationship to Other Models

- Uses entities: KPIRecord, PerformanceSummary, IncidentSummary, EnergyCostSummary, ProgrammeRecord.
- Informs:
  - `ERAGS-MOD-KPI-002_KPI_Calculation_and_Data_Lineage_Model.md`
  - `ERAGS-MOD-KPI-003_Governance_Decision_Rules_and_Thresholds_Model.md`
- Implementing artefact for:
  - ERAGS-F-008, ERAGS-D-002, ERAGS-D-003, ERAGS-NF-006.
