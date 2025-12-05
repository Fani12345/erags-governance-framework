---
DocID: ERAGS-MOD-ARCH-001
Title: ERAGS System Context Model
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
  - ERAGS-DOC-CTX-001
  - ERAGS-DOC-STK-001
  - ERAGS-DOC-POL-001
  - ERAGS-DOC-STR-001
  - ERAGS-DOC-PROC-OV-001
  - ERAGS-REQ-HL-001
RelatedFolders:
  - requirements/
  - processes/
  - data/
---

# ERAGS System Context Model

## 1. Purpose

This model describes the **system context** for ERAGS within the wider National Roads Electrical & Electronic Operations System (NRE²OS). It identifies:

- The external actors and subsystems that interact with ERAGS.
- The key information exchanged between ERAGS and each external party.
- The boundaries of responsibility for System 1 (ERAGS).

The context model supports functional requirements ERAGS-F-001 to ERAGS-F-008, interface requirements in ERAGS-REQ-IF-001 and regulatory requirements ERAGS-R-001 to ERAGS-R-003.

## 2. System-of-Interest: ERAGS

ERAGS is the **governance and strategy subsystem** responsible for:

- Asset management policies for road lighting, traffic signals and associated electrical assets.
- Lifecycle strategies, performance targets and levels of service.
- Governance processes for programme approval, change control and continuous improvement.
- Requirements and performance expectations for other subsystems (for example CMMS/WFM, GIS, Analytics).

ERAGS does not execute field work itself; instead, it directs and constrains operational subsystems.

## 3. External Actors and Subsystems

The main external entities interacting with ERAGS are:

1. **Roads Directorate Executive Management**
   - Approves policies, strategies and major programmes.
   - Receives performance reports and recommendations.

2. **Electrical Section Management and Supervisors**
   - Use ERAGS policies, strategies and programmes to plan and manage the electrical section.
   - Provide feedback on feasibility, risks and operational constraints.

3. **Human Resources and Competence Management System (System 2)**
   - Manages staff competencies, authorisations and training.
   - Receives governance requirements on competence and authorisation policies.

4. **HSE and Incident Management System (System 3)**
   - Manages safety procedures, incidents and corrective actions.
   - Provides aggregated incident and risk data to ERAGS.

5. **Asset Inventory and GIS System (System 4)**
   - Maintains geo-referenced asset registers.
   - Provides asset summaries and spatial data to ERAGS.
   - Receives data requirements from ERAGS.

6. **Maintenance and Operations Management (CMMS/WFM) System (System 5)**
   - Plans and records maintenance and operational tasks.
   - Provides fault, work-order and performance data.
   - Receives approved programmes and priorities from ERAGS.

7. **Street-Lighting Design and Energy Management System (System 6)**
   - Performs lighting designs and energy analyses.
   - Provides energy performance insights.
   - Receives strategic direction on levels of service and energy efficiency.

8. **Traffic Signal Engineering and Operations System (System 7)**
   - Designs and operates traffic signal control.
   - Provides signal performance data and engineering insights.
   - Receives governance requirements for safety and performance.

9. **Security, Vandalism and Damage Management System (System 8)**
   - Manages vandalism/theft/damage events and responses.
   - Provides risk and cost data for hotspots.
   - Receives strategic guidance on resilience and anti-vandalism measures.

10. **Data, Analytics, KPI and Continuous Improvement System (System 9)**
    - Aggregates and analyses data from operational systems.
    - Produces dashboards, trends and risk indicators.
    - Receives KPI definitions and targets from ERAGS.

11. **External Oversight and Audit Bodies**
    - May review ERAGS policies, strategies and decision records.
    - Receive evidence of compliance and performance.

12. **Public and Road Users (Indirect)**
    - Provide complaints, feedback and perceived service levels through other subsystems.
    - Are the ultimate beneficiaries of safe and reliable lighting and signals.

## 4. Information Flows (High-Level)

At a high level, the context model includes the following information exchanges:

- **From ERAGS to others:**
  - Asset Management Policy and supporting governance policies.
  - Asset Strategy, including levels of service, lifecycle strategies and priorities.
  - Performance targets and KPI definitions.
  - Approved annual and multi-year programmes and investment priorities.
  - Governance requirements on competence, safety, asset data and reporting.

- **To ERAGS from others:**
  - Asset register and spatial data (from GIS).
  - Performance data and work history (from CMMS/WFM).
  - Energy and cost data (from Finance and energy management functions).
  - Incident and safety data (from HSE).
  - Vandalism and damage statistics (from Security and related systems).
  - Analytical reports and KPI dashboards (from Analytics).
  - Feedback on feasibility and implementation constraints (from Electrical Section management).

These flows are detailed further in `models/04_information_flows/ERAGS-MOD-FLOW-001_External_Information_Flows.md`.

## 5. Boundary Clarification

The **boundary** of ERAGS is defined as:

- **Inside ERAGS:**
  - Definition and approval of policies and strategies.
  - Definition and maintenance of governance requirements and RTM.
  - Governance process design and change-control rules.
  - Interpretation of performance data at governance level and decision-making based on that data.

- **Outside ERAGS:**
  - Execution of maintenance, operation and project work.
  - Detailed technical design of installations (except to the extent that ERAGS sets standards).
  - Day-to-day task assignment and supervision of individual crews.
  - Low-level data capture and storage in operational systems.

Clarifying these boundaries helps ensure that System 1 is not overloaded with operational detail and that subordinate subsystems have clear responsibilities.

## 6. Traceability to Requirements

This context model supports, among others:

- **ERAGS-F-001 to ERAGS-F-008** – by identifying the environment where policies, strategies, processes and KPIs operate.
- **ERAGS-D-001 to ERAGS-D-003** – by indicating where governance-relevant data originates.
- **ERAGS-R-001 to ERAGS-R-003** – by showing the external bodies and systems through which regulatory compliance must be demonstrated.
- **Interface requirements ERAGS-IF-101..ERAGS-IF-502** – by explicitly naming external subsystems that interfaces target.

These requirement IDs will be referenced in the RTM entry for this model.

## 7. Diagram Reference (Optional)

A graphical context diagram may be created and stored as:

- `models/01_architecture/ERAGS-MOD-ARCH-001_System_Context_Diagram.png`

This Markdown file shall then embed or link that diagram. For now, this textual description serves as the authoritative context model.
