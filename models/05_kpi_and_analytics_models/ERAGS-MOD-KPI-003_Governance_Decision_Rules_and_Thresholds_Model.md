---
DocID: ERAGS-MOD-KPI-003
Title: ERAGS Governance Decision Rules and Thresholds Model
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
  - ERAGS-MOD-KPI-002
  - ERAGS-MOD-FLOW-002
  - ERAGS-DOC-PROC-OV-001
  - ERAGS-MOD-PROC-002
  - ERAGS-MOD-PROC-003
RelatedFolders:
  - models/02_process_models/
  - qa/
---

# ERAGS Governance Decision Rules and Thresholds Model

## 1. Purpose

This document defines:

- Thresholds and target bands for key KPIs.
- Governance decision rules that specify what should happen when KPIs deviate from targets.
- How KPI deviations trigger governance processes in ERAGS.

It operationalises ERAGS-F-008 (Performance and KPI Management) and ERAGS-NF-006 (Governance Performance Monitoring), and links performance measurement to governance actions.

## 2. Threshold Concepts

- **Target** – Desired KPI level under normal conditions.
- **Warning Threshold** – Level at which attention and monitoring should increase.
- **Intervention Threshold** – Level at which a formal governance process must be initiated (for example strategy or programme review).
- **Critical Threshold** – Level requiring urgent action.

Thresholds may be:

- Absolute values (for example availability ≥ 98%).
- Relative changes (for example 5% deterioration compared to prior year).

## 3. KPI Threshold Examples

### 3.1 Lighting Availability (KPI-AV-001)

Example for system-wide view (illustrative; real values to be defined with stakeholders):

- Target: ≥ 98.5%  
- Warning Threshold: < 98.5%  
- Intervention Threshold: < 97.5%  
- Critical Threshold: < 96.0%

### 3.2 Traffic Signal Availability (KPI-AV-002)

For critical intersections:

- Target: ≥ 99.8%  
- Warning Threshold: < 99.8%  
- Intervention Threshold: < 99.5%  
- Critical Threshold: < 99.0%

### 3.3 Mean Time to Repair (KPI-RT-001)

For high-priority faults:

- Target: ≤ 8 hours  
- Warning Threshold: > 8 hours  
- Intervention Threshold: > 12 hours  
- Critical Threshold: > 24 hours

### 3.4 Safety Incident Rate (KPI-SF-001)

- Target: 0 severe incidents.
- Intervention Threshold: any severe incident.
- Warning Thresholds for minor incidents to be set based on historical rates.

(Exact numeric values are policy/strategy decisions; this model defines the structure.)

---

## 4. Governance Decision Rules

### 4.1 Rule Structure

Each rule is expressed as:

- Rule_ID
- Trigger_Condition (KPI deviation and context)
- Required_Action
- Responsible_Component
- Responsible_Role
- Related_Process

### 4.2 Example Rules

#### Rule R-KPI-001 – Lighting Availability Warning

- **Rule_ID:** R-KPI-001  
- **Trigger_Condition:**  
  - KPI-AV-001 (Lighting Availability) < Target for two consecutive monthly periods at system-wide level.  
- **Required_Action:**  
  - Performance & KPI Management Component flags issue to Strategy Management and Governance Process Management.  
  - Increased monitoring and analysis required; no immediate programme changes mandated.  
- **Responsible_Component:** Performance and KPI Management Component.  
- **Responsible_Role:** Performance and KPI coordinator (within Electrical Section governance).  
- **Related_Process:** Performance review in ERAGS-DOC-PROC-OV-001.

#### Rule R-KPI-002 – Lighting Availability Intervention

- **Rule_ID:** R-KPI-002  
- **Trigger_Condition:**  
  - KPI-AV-001 < Intervention Threshold for any area or corridor for two consecutive monthly periods.  
- **Required_Action:**  
  - Governance Process Management initiates a “Targeted Strategy and Programme Review” for affected area.  
  - Strategy Management evaluates options (e.g. intensified maintenance, targeted upgrades).  
- **Responsible_Component:** Governance Process Management; Strategy Management.  
- **Related_Process:** Programme and Investment Governance (ERAGS-MOD-PROC-003).

#### Rule R-KPI-003 – Traffic Signal Critical Incident

- **Rule_ID:** R-KPI-003  
- **Trigger_Condition:**  
  - KPI-AV-002 at a critical intersection < Critical Threshold in any monthly period, or a serious incident is recorded related to signal failure.  
- **Required_Action:**  
  - Immediate escalation to Electrical Section management and HSE.  
  - Short-term remedial plan and review of design, maintenance and operations at affected intersection.  
- **Responsible_Component:** Performance & KPI Management; Strategy Management; Data & Information Integration.  
- **Related_Process:** Incident-driven strategy review process defined in `/processes`.

#### Rule R-KPI-004 – Safety Incident

- **Rule_ID:** R-KPI-004  
- **Trigger_Condition:**  
  - Any severe safety incident (as defined by IncidentSummary.SeverityIndex) involving electrical roads assets.  
- **Required_Action:**  
  - HSE-led incident review, with ERAGS participation.  
  - Consider policy and strategy implications; possible revision of design standards, maintenance strategy or operational procedures.  
  - Record decision and rationale in DecisionLogEntry.  
- **Responsible_Component:** Governance Process Management; Policy Management; Strategy Management.  
- **Related_Process:** Safety incident governance process.

#### Rule R-KPI-005 – Energy Efficiency Programme Trigger

- **Rule_ID:** R-KPI-005  
- **Trigger_Condition:**  
  - KPI-EN-001 deteriorates (increases) beyond Warning Threshold for three consecutive years, or stays above Target by a significant margin.  
- **Required_Action:**  
  - Strategy Management investigates need for enhanced energy-efficiency programmes (for example further LED retrofits, dimming strategies).  
- **Responsible_Component:** Strategy Management; Analytics Interface.  
- **Related_Process:** Programme and Investment Governance.

---

## 5. Interaction with Internal Information Flows

When rules are triggered:

- Performance and KPI Management sends alerts and KPIRecord sets to:
  - Strategy Management.
  - Governance Process Management.
- Governance Process Management:
  - Initiates appropriate governance processes (policy review, strategy review, programme review).
- Document and Configuration Management:
  - Ensures resulting decisions and document updates are recorded correctly.

These flows align with `ERAGS-MOD-FLOW-002_Internal_ERAGS_Information_Flows.md`.

---

## 6. Relationship to QA and Audit

- QA checks can verify:
  - For each KPI deviation beyond Intervention Threshold:
    - Confirm that a corresponding governance process was initiated.
    - Confirm existence of DecisionLogEntry for resulting decisions.
- Auditors can:
  - Trace from KPIRecord to rules in this document.
  - Check consistency between rules, actual actions taken and recorded decisions.

---

## 7. Relationship to Requirements and RTM

This model is an implementing artefact for:

- ERAGS-F-008 – Performance and KPI Management.
- ERAGS-D-002, ERAGS-D-003 – Performance data and data quality.
- ERAGS-R-003 – Documentation and Auditability.
- ERAGS-NF-006 – Governance performance monitoring.

It should be referenced accordingly in `ERAGS_RTM.csv`.
